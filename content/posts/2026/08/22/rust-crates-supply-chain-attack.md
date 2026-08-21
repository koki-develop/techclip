---
date: "2026-08-22T02:06:56+09:00"
title: "Rustの人気クレートarrayrefらがサプライチェーン攻撃の標的に、ビルド時に実行される偽装パッケージでインフォスティーラーを配布"
description: "累計2億4500万ダウンロード超のRustクレートarrayrefなど3パッケージの開発者アカウントが侵害され、proc-macro2を装う偽パッケージ「proc-macro1」を通じてビルド時にインフォスティーラーが実行される事態が発生した。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/08/rust-supply-chain-attack-puts-build.html"
  - "https://www.bleepingcomputer.com/news/security/hackers-poison-arrayref-rust-crate-to-push-infostealer-malware/"
  - "https://www.theregister.com/security/2026/08/21/hackers-poison-popular-rust-crates-to-steal-developers-credentials/5291075"
---

## 概要

2026年8月20日、Rustのクレートエコシステムで深刻なサプライチェーン攻撃が発生した。累計2億4500万ダウンロード超を誇る人気クレート「arrayref」と、同じ開発者(David Roundy氏)が保守する「internment」「append-only-vec」の3パッケージに、不正な依存関係が仕込まれたバージョン(それぞれ0.3.10、0.8.7、0.1.9)が公開された。Rustセキュリティレスポンスチームは、開発者本人が悪意を持って行動したのではなく、そのアカウントないし端末が侵害されたとみている。攻撃者は事前に、人気クレート「proc-macro2」の開発者として知られるdtolnay氏になりすました偽アカウント(crates.io ID 438608)をGitHub上に用意しており、これを使ってproc-macro2を模したタイポスクワットパッケージ「proc-macro1」を配布。これをarrayrefらの新バージョンに依存関係として追加することで、ビルド時に不正コードが自動実行される仕組みを作り上げていた。

## 攻撃の手口とタイムライン

攻撃はUTCで8月20日未明から進行した。01:17に偽のdtolnayアカウントが作成され、01:55にはまず無害なproc-macro1バージョン(1.0.106)が公開されて信頼性を装った。その後07:11に悪性版(1.0.107)が公開され、07:15にはarrayref 0.3.10が正規(だが侵害された)アカウントから公開されると同時に、旧バージョン0.3.5〜0.3.9が一斉にyank(取り下げ)された。これにより、依存関係を更新した開発者は悪性版以外を選べない状態に追い込まれた。internmentとappend-only-vecでも同様の手口が使われている。

proc-macro1に仕込まれたbuild.rsスクリプトは、コンパイル時に自動実行される点が悪質で、ランタイム側で何らかの関数を呼び出す必要すらなかった。スクリプトはOSとCPUアーキテクチャを判定した上で、base64断片から再構成したC2アドレスからLinux・Windows・Intel Mac・Apple Siliconそれぞれ向けのペイロードをダウンロードして実行する。Unix系では`/tmp/rust-setup`に書き込んで実行権限を付与しバックグラウンド実行し、WindowsではTLS証明書検証を無効化した上で`%TEMP%\rust-setup.ps1`を隠しウィンドウのwscript.exe経由で実行していた。

セキュリティ企業Aikidoの調査によれば、第2段階のペイロードはChrome・Brave・EdgeなどChromiumベースのブラウザからSQLiteデータベース経由で認証情報を窃取するほか、暗号資産ウォレットの拡張機能も標的としていた。永続化にはWindowsのレジストリRunキー、macOSのLaunchAgent、LinuxのsystemdといったOSごとの手法が使い分けられており、C2との通信やリモートコマンド実行にも対応した本格的なインプラントだったという。研究者は、このインフラが過去に発覚した北朝鮮系サプライチェーン攻撃(npmのMastraやaxiosを狙った事案など)と重複していると指摘している。

## 影響と対応

各パッケージの公開時間は86分〜107分と短く、Rustチームはインシデント報告(07:54)を受けてから短時間でproc-macro1をcrates.ioから削除(08:03)、arrayref 0.3.10もインデックスから除去(08:41)した。関連するタイポスクワットパッケージ(proc-macro-en、aovine、arone、aronenao、tinymemberなど)も併せて削除されている。The Hacker Newsによれば、実際にマルウェアが実行された確証は今のところ確認されていないというが、Rustチームは該当バージョンをインストールした開発者に対し、システムが侵害された前提で対応するよう呼びかけている。具体的には、認証情報・CIトークン・署名鍵をすべてローテーションし、安全なバックアップから環境を再構築すること、またCargoのロックファイルやローカルキャッシュを監査することが推奨されている。今回の発見にはセキュリティ企業Nextron SystemsとAikidoが貢献した。
