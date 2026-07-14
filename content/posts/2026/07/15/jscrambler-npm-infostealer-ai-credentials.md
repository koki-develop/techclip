---
date: "2026-07-15T02:30:03+09:00"
title: "難読化ツールJscrambler、npmパッケージ改ざんでRust製マルウェアがAI開発ツールの認証情報を標的に"
description: "JavaScript難読化ツールJscramblerの複数npmパッケージが侵害され、AWSやAIコーディングツールの認証情報を狙うRust製インフォスティーラーが混入した。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/07/compromised-jscrambler-8140-npm-release.html"
  - "https://www.bleepingcomputer.com/news/security/hackers-backdoor-jscrambler-npm-package-with-infostealer-malware/"
  - "https://www.securityweek.com/multiple-jscrambler-packages-impacted-by-supply-chain-attack/"
---

## 概要

JavaScript難読化ソリューションを提供するJscrambler社のnpmパッケージが7月11日、サプライチェーン攻撃の被害に遭った。攻撃者は盗んだnpm発行認証情報を使い、正当なメンテナーアカウントから通常のリリースフローを迂回する形でパッケージを直接改ざん・公開した。影響を受けたのは主要パッケージの8.14.0、8.16.0、8.17.0、8.18.0、8.20.0の各バージョンで、加えてJscrambler-webpack-plugin、gulp-Jscrambler、grunt-Jscrambler、Jscrambler-metro-pluginといった関連パッケージにも波及した。悪意あるバージョンにはインストール時に実行されるpreinstallフックが仕込まれており、Windows・macOS・Linuxそれぞれに対応したプラットフォーム別バイナリがドロップされる仕組みになっていた。

セキュリティ企業のSocketが公開からわずか6分後にこのリリースに警告フラグを立て、侵害を検出した。悪質なパッケージは公開から廃止までの約2時間で1,479回ダウンロードされたことが確認されている。Jscrambler社は7月13日に事態を公表し、npm発行認証情報を取り消した上でセキュリティ管理体制を強化した。

## 技術的な詳細

混入したマルウェアは「IronWorm」と呼ばれるRust製のインフォスティーラーで、ChaCha20-Poly1305暗号化アルゴリズムによる強力な難読化が施されており、解析による特定が困難な作りになっていた。狙われた認証情報の範囲は広く、AWS・Azure・Google Cloudなどのクラウド認証情報、MetaMaskやPhantom、Exodusといった暗号資産ウォレット、Bitwardenのパスワード管理データ、Git/SSH鍵や環境変数などの開発者秘密情報、さらにブラウザに保存されたパスワードやDiscord・Slack・Telegramのセッション情報にまで及んだ。

特に注目されるのは、Claude Desktop、Cursor、VS CodeといったAIコーディングアシスタント関連の設定・認証情報も収集対象に含まれていた点で、AI開発ツールがサプライチェーン攻撃の新たな標的として明確に狙われたことを示している。マルウェアはC2サーバー（IPアドレス 37.27.122.124、57.128.246.79）と通信する構成になっていた。

## 対応策

Jscrambler社および各セキュリティ研究者は、影響を受けた可能性のある開発者に対して以下の対応を推奨している。まず、パッケージを安全なバージョンである8.15.0または8.22.0にアップグレードし、ロックファイルから該当する侵害バージョンの記述を削除する必要がある。さらに、悪意あるバージョンをインストールした形跡があるマシンについては環境がコンプロマイズされたものとみなし、AWSやクラウドサービス、暗号資産ウォレット、AI開発ツールを含むあらゆる認証情報を速やかにリセットすることが求められている。また、前述のC2 IPアドレスへの通信をファイアウォールやネットワーク監視でブロックすることも有効な対策として挙げられている。

今回の事件は、正規のメンテナーアカウントが侵害された場合、通常のコードレビューやリリースプロセスをすり抜けてマルウェアが配布され得ることを改めて示した。加えて、AIコーディングツールの認証情報が明確な攻撃対象になっている点は、開発者のワークフローに深く組み込まれつつあるAIツールのセキュリティ管理が今後より重要になることを示唆している。
