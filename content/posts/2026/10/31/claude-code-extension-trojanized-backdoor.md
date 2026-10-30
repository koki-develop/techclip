---
date: "2026-10-31T08:07:33+09:00"
title: "Claude Code拡張機能がCursor Marketplaceで改ざん、SSHバックドア設置も実装ミスで多くは不発に"
description: "Cursor Marketplaceで配布された公式Claude Code拡張機能の改ざん版が永続的なSSHバックドアを設置し最大5000人に影響したが、コードの欠陥により遠隔アクセスの多くは成立しなかった。"
tags:
  - AI
  - Security
references:
  - "https://thehackernews.com/2026/10/official-claude-code-vs-code-extension.html"
  - "https://www.bleepingcomputer.com/news/security/malicious-claude-code-extension-on-cursor-planted-ssh-backdoors/"
  - "https://www.theregister.com/cyber-crime/2026/10/30/anthropic-that-claude-code-extension-compromise-couldnt-be-us/5306682"
---

## 概要

Cursorの開発者向けマーケットプレイスで配布されていたAnthropic公式の「Claude Code」拡張機能(バージョン2.1.313)が改ざんされ、永続的なSSHバックドアを設置するマルウェアが混入した状態で公開されていたことが明らかになった。公開期間は太平洋時間2026年10月29日午前2時27分から午後1時35分までの約11時間(UTCでは同日9時27分から20時35分)で、最大5000人の開発者がこの改ざん版をインストールした可能性があるという。異常を検知したCursorは悪意あるバージョンを即座に削除し、マーケットプレイス全体を一時閉鎖。Anthropicは修正版(v2.1.314)をOpen VSXとMicrosoft VS Code Marketplaceで公開した。

## 侵入の手口と技術的な仕組み

マルウェアは拡張機能本体の`extension.js`ファイルの先頭に約66行のJavaScriptローダーを挿入する形で混入していた。正規のコード自体は書き換えられておらず、拡張機能の読み込み時にローダーが自動実行される仕組みで、ユーザー側の操作は不要だった。実行されると、ユーザー名やホスト名、公開IPアドレス、Gitのメールアドレスに加え、名称に「KEY」「TOKEN」「SECRET」「PASS」「AWS」「GCP」などを含む環境変数名を最大40個まで収集し、攻撃者が管理するサーバー「134.209.82.225」へ送信していた。さらに「svc-telemetry」というラベル付きの攻撃者公開鍵を`~/.ssh/authorized_keys`に追加し、同サーバーへの逆SSHトンネルを確立。Windowsではスケジュールタスク、Linuxではcrontab、macOSではLaunchAgentを使って永続化を図り、約1分おきにトンネルの再接続を試みる設計だった。

## 実害を限定した実装ミス

一方で、セキュリティ研究者らはこのバックドアのSSH設定ルーチンに重大な欠陥があり、多くの被害者では遠隔アクセスが実際には成立しなかった可能性が高いと指摘している。Windows環境では、マルウェアがPowerShell経由でOpenSSHサーバーをインストールしようとする際にUnixシェル「/bin/sh」の呼び出しを前提としており、標準的なWindows環境では動作しない。macOS環境でも、管理者権限なしにSSHの稼働状態を確認しようとしてエラーとなり、処理がスキップされる仕組みになっていた。EDRベンダーのPhorionやOpenSourceMalwareの研究者も同様の指摘をしており、Cursorはこの分析を引用し「管理者権限が必要なため実害は限定的だった」と説明している。また、収集された環境変数は名称のみで、認証情報の値そのものは直接窃取されておらず、攻撃者がSSHトンネル経由で手動で情報を取得する意図だったとみられる。

## 責任の所在と対応状況

Anthropicの技術スタッフFelix Riesebergは「悪意ある行為者がCursorのマーケットプレイスにアクセスし改ざん版を公開した」とし、Anthropic公式チャネルで配布されたバージョンには影響がないと強調した。一方Cursorは、悪意あるバージョンが約11時間利用可能だったことを認め、検知後は該当バージョンの削除、マーケットプレイスの一時閉鎖、セキュリティキーのローテーション、攻撃者サーバーへの接続遮断、ホスティング事業者と連携したサーバーの停止などの対応を取ったと説明している。ただし、攻撃者がどのような経路でAnthropic名義の拡張機能をマーケットプレイスに改ざん版として公開できたのかについては、両社とも詳細を明らかにしていない。Cursorは内部調査で他の拡張機能への影響はないと確認し、影響を受けた可能性のあるユーザーには個別に連絡する予定としている。被害の可能性があるユーザーには、`~/.ssh/authorized_keys`内に「svc-telemetry」というラベルの鍵がないか確認し、該当端末の隔離、認証情報の無効化、セッションの失効、安全なバックアップからの環境再構築を行うことが推奨されている。
