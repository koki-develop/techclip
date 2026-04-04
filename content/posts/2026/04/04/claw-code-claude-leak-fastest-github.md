---
date: "2026-04-04T10:37:37+09:00"
title: "Claude Codeソースコード誤公開事件：npmの設定ミスで51万行が流出、再実装版「Claw Code」がGitHub史上最速成長リポジトリに"
description: "Anthropicのnpmパッケージに`.npmignore`設定漏れでClaude Codeのソースコード約51万行が誤公開され、それを基にしたオープンソース再実装「Claw Code」がGitHub史上最速で10万スターを突破した。"
tags:
  - OSS
  - AI
references:
  - "https://www.24-7pressrelease.com/press-release/533389/claw-code-launches-open-source-ai-coding-agent-framework-with-72000-github-stars-in-first-days"
  - "https://cybernews.com/tech/claude-code-leak-spawns-fastest-github-repo/"
  - "https://layer5.io/blog/engineering/the-claude-code-source-leak-512000-lines-a-missing-npmignore-and-the-fastest-growing-repo-in-github-history/"
---

## 事の発端：`.npmignore`の記述漏れによる大規模リーク

2026年3月31日、AnthropicがClaude Codeのnpmパッケージ（バージョン2.1.88）を更新した際に、重大なパッケージング上のミスが発生した。`.npmignore`の記述が不完全だったため、59.8MBのソースマップがパッケージに同梱されてしまい、約1,900ファイル・512,000行にのぼる未難読化のTypeScriptソースコードが誰でもダウンロードできる状態で公開された。

このリークで明らかになった内部実装には、コンテキストウィンドウの制限を乗り越えるための「自己修復メモリアーキテクチャ」、`KAIROS`と呼ばれる永続的なバックグラウンドエージェント機能、OSSプロジェクトへの隠密コントリビューションを行う「Undercover Mode」など、これまで公開されていなかった機能が含まれていた。セキュリティ研究者は、内部データフローの詳細が露わになったことで、従来のジェイルブレイク手法に依存しない新たな攻撃ベクターが生まれると警告している。

## GitHub史上最速成長リポジトリの誕生

このリークに着目したのが研究者のSigrid Jin（GitHubアカウント: instructkr）だ。彼はリークされたコードを参照しつつ、プロプライエタリなコードを一切使用しない「クリーンルーム実装」として、PythonとRustによる再実装プロジェクト「Claw Code」を立ち上げた。プロジェクトは公開後急速に成長し、初期の数日間で72,000スター・72,600フォークに到達した後、10万スターを突破。GitHub史上最も速く成長したリポジトリの一つとなった。

プロジェクトの製作者は「ハーネス、つまりコンテキストの流れ方、ツールの接続方法、意思決定の仕組みこそが本当のエンジニアリングが宿る場所だ」とコメントしており、LLMと開発ツールを結ぶ透明で監査可能なインフラを提供することを目的として掲げている。Python実装のワークスペースコード、テストディレクトリ、CLIユーティリティが公開されており、本番環境向けのRust実装も開発中だ。

## AnthropicのDMCA対応とセキュリティへの波及

Anthropicはリーク発覚後、GitHubに対してDMCAによる削除要請を行い、リークコードを直接含むリポジトリの排除に動いた。しかし、Claw CodeはクリーンルームのPython/Rust実装として設計されているため、単純なDMCA対象にはなりにくいとみられている。

一方、この騒動に便乗する形で、Vidar StealerやGhostSocksといったマルウェアを仕込んだ、Claude Codeのリークコードを装った偽リポジトリが流通し始めたことも報告されている。人気リポジトリへの注目を悪用したサプライチェーン攻撃のリスクが顕在化しており、ユーザーは公式GitHubリポジトリ（github.com/instructkr/claw-code）以外のソースからダウンロードしないよう注意が必要だ。今回の事件は、npmパッケージ管理における`.npmignore`や`.files`フィールドの設定ミスが引き起こすリスクを改めて業界に示すものとなった。
