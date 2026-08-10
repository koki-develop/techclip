---
date: "2026-08-11T02:16:29+09:00"
title: "npmに約800個の悪意あるパッケージ、AI悪用のタイポスクワッティングでクロスプラットフォームRAT「WEL1DROPPER」拡散"
description: "npmレジストリで「Flooding Dropper」と呼ばれるキャンペーンが発覚し、AIを使ったタイポスクワッティングで公開された約800個の悪意あるパッケージがWindows・Mac・Linuxを狙うRAT兼情報窃取マルウェア「WEL1DROPPER」を配布していた。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/08/nearly-800-malicious-npm-packages.html"
  - "https://www.sonatype.com/blog/flooding-dropper-hits-npm-with-850-malicious-packages"
  - "https://opensourcemalware.com/blog/russian-ai-slopsquatting-npm-campaign"
---

## 概要

npmレジストリ上で、約800〜850個にのぼる悪意あるパッケージが公開され、Windows・macOS・Linuxの全プラットフォームを標的とするクロスプラットフォーム型のRAT(リモートアクセス型トロイの木馬)兼情報窃取マルウェア「WEL1DROPPER」を配布していたことが発覚した。このキャンペーンはセキュリティ企業Sonatypeにより「Flooding Dropper」と命名され、sonatype-2026-005660として追跡されており、CVSS 8.7・CWE-506に分類される深刻な脅威とされている。発端はOpenSourceMalwareの研究者Paul McCartyが「bigops-backend」という不審なパッケージを報告したことで、その後Sonatype Research Labs(Jorge Cardona氏ら)がわずか48時間で700個以上のパッケージが同一インフラから配布されていることを突き止め、大規模キャンペーンの全容が明らかになった。

## AIを悪用したタイポスクワッティングの手口

攻撃者は「AI slopsquatting」と呼ばれる手法を用い、AIで大量生成したランダムなタイポスクワッティング名でパッケージを量産した。「bigops」や「bnpl」(後払い決済)といった単語を組み合わせた「bigops-api」「checkout-mobile-bnpl」「dolyame-boxy-desktop-bnpl-card-gallery」などの名称が確認されており、多くは正当な決済・チェックアウト向けSDKを装っている。特徴的なのは、従来型のマルウェア入りパッケージが悪用してきたnpmのpreinstall/postinstallといったライフサイクルフックを一切使わない点で、代わりに「lib/telemetry.js」や「_helpers.js」といった一見無害な計測用SDKを装ったファイルに悪意あるコードを隠し、パッケージがrequire()/importで読み込まれた瞬間に発火する仕組みになっている。多くのパッケージが「35.x.y」という共通のバージョン範囲を持ち、単一のアカウントではなく多数の自動生成されたnpmアカウントから分散的に公開されていたことも、大規模かつ組織的な攻撃であることを裏付けている。

## 感染チェーンと技術的詳細

感染は多段階で進行する。第一段階のJavaScriptローダーがホストのOSとCPUアーキテクチャを判定した上で、3つのCloudflare Workersホストを経由したHTTPS通信でペイロードを取得し、失敗時にはBase64エンコードされたDNS TXTレコードによるフォールバック経路で「wel1[.]ru」ドメイン配下から取得する。配信ドメインはプラットフォームごとに使い分けられており、Linux x64は「sdk.dl.wel1[.]ru」、Linux ARM64は「ext.dl.wel1[.]ru」、macOSは「pkg.dl.wel1[.]ru」、Windowsは「net.dl.wel1[.]ru」となっている。取得したバイナリは親プロセスから切り離された(detached)状態で実行されるため、インストールプロセスが終了した後も動作を継続する。

OS別のペイロードも高度な回避機能を備える。Windows版はEvent Tracing for Windows(ETW)やAntimalware Scan Interface(AMSI)をパッチして検知を無効化し、デバッガや仮想環境・サンドボックスを検出した上で、暗号化されたペイロード(/pkg/update_win.exe)をメモリ上にリフレクティブロードし、レジストリのRunキーとスケジュールタスクで永続化する。macOS版はlldb・dtrace・Frida・Wireshark・VMwareなどの解析ツールを検出する回避機構を持ち、LaunchAgent(com.apple.windowserver.helper.plist)経由で永続化した上で追加のビーコン(/pkg/beacon_mac.bin)を取得する。Linux版はUPXでパックされたELFバイナリで、オープンソースC2フレームワーク「Sliver」を配布するとみられる(Sonatypeは最終段階のペイロードがSliverであることを未確認としている)。さらに一時ファイルには「.cache_」「dotnet_diag_」など正規プロセスを装う名前が付けられ、6時間のレート制限を設けることで検出を回避する工夫も施されている。

## ロシアとの関連性、そして今後の対策

macOS向けペイローク内には「tcsbank[.]ru」や「cloudpayments[.]ru」といったロシアの金融機関・決済サービスのドメインが埋め込まれており、ロシア国内のユーザーや金融セクターを標的にした攻撃である可能性が指摘されている。本キャンペーンは、2026年4月から5月にかけて250以上の悪意あるパッケージを公開した依存関係混同(dependency confusion)型キャンペーン「Moika」の後継、あるいは進化形とみられている。なお同時期にはUnit 42が、暗号資産窃取マルウェアを配布する別のnpmパッケージ群や、npm・PyPIを通じたクラウド認証情報の窃取、EtherHiding型C2ドロッパー、Solanaウォレット窃取、さらにはブラウザを商用プロキシネットワークの一部に組み込む悪意あるChrome拡張機能なども並行して確認しており、オープンソースエコシステム全体を狙った攻撃が広範囲に展開されている実態が浮かび上がっている。

Sonatypeは、感染が疑われる組織に対し、対象システムの隔離と既知の永続化メカニズムの捜索、プロセス・DNS・プロキシのテレメトリ調査、すべての開発者認証情報のローテーション、内部キャッシュやコンテナレイヤーからの感染パッケージの除去、そして新規パッケージ導入時の綴りの入念な確認を推奨している。今回の事例が示す最大の教訓は、「npmのライフサイクルスクリプトをブロックするだけでは不十分」という点だ。悪意あるコードはインストール時ではなくインポート時まで実行を遅らせることで、従来型の防御をすり抜けてしまう。開発者はサプライチェーンセキュリティ対策として、依存関係のスキャンだけでなく、実行時の挙動監視も含めた多層的な防御を検討する必要がある。
