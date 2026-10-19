---
date: "2026-10-20T08:12:22+09:00"
title: "Microsoft、rustup風の.NETツールチェーン管理ツール「dotnetup」をプレビュー公開"
description: "Microsoftが.NET SDK/ランタイムを管理者権限なしで複数バージョン管理できる新ツール「dotnetup」のパブリックプレビューを公開した。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/dotnet/introducing-dotnetup/"
---

## 概要

Microsoftは10月15日、.NET SDKおよびランタイムのインストールと管理を行う新ツール「dotnetup」のパブリックプレビューを公開した。Rust向けの「rustup」やNode.js向けの「nvm」に着想を得たツールチェーンマネージャーで、管理者権限を必要とせずユーザーディレクトリ内に複数バージョンの.NETを並行してインストール・切り替えできる点が特徴だ。現時点ではmacOSとLinuxに対応しており、Windowsのシステムレベルインストール管理は今後の対応となる。

従来、.NET環境の構築にはシステムのパッケージマネージャー、tarball展開、インストールスクリプト（dotnet-install.sh）など複数の手段が併存しており、権限まわりの制約やインストール済みファイルの散在が課題となっていた。dotnetupはこれらを単一のクロスプラットフォームCLIに統合し、OSを問わず共通の操作体験を提供することを目指している。

## 主な機能とインストール方法

dotnetupはmacOSではZsh経由で`curl -fsSL https://aka.ms/dotnetup/get-dotnetup.sh | zsh`、Linuxでは同スクリプトを`bash`で実行、Windowsでは`irm https://aka.ms/dotnetup/get-dotnetup.ps1 | iex`というPowerShellコマンドでそれぞれ導入し、`dotnetup init`で初期化する。導入後は`dotnetup list`でインストール済みのSDK・ランタイムを一覧表示し、`dotnetup update`で追跡中のチャネルを最新版に更新できるほか、`dotnetup sdk install preview`や`dotnetup runtime install daily`のようにプレビュー版や日次ビルドを個別に指定してインストールすることも可能だ。ツール自体のアップデートは`dotnetup self update`で行う。

メジャーバージョン単位での追跡による自動更新や、プロジェクトの`global.json`で指定されたSDKバージョンを尊重する機能も備える。既存のdotnet-install.shと比べると、インストール済みSDK/ランタイムの管理機能に加えて署名・チェックサムによる検証、複数バージョンをまとめて導入する際の高速化など、単なる導入スクリプトではなくツールチェーン全体を管理するマネージャーとしての性格が強い。管理者権限なしでノンインタラクティブに実行できるため、コンテナ化されたCI/CDワーカーでの利用にも適している。

## 今後の展望

現在のプレビュー版はmacOSとLinuxが対象で、Windowsにおけるシステムレベルのインストール管理（管理者権限を用いたインストール)は今後のロードマップに位置付けられている。Microsoftは今後、GitHub ActionsやAzure DevOpsとの統合、ユーザー体験の改善、さらにAIエージェントとの連携強化も計画していると述べている。詳細な利用方法はMicrosoft Learnの公式ドキュメントで、フィードバックはGitHubの「dotnet/sdk」discussionsで受け付けている。rustupやnvmが各言語エコシステムで標準的なツールとして定着した経緯を踏まえると、dotnetupが.NET開発者の環境構築体験をどこまで簡素化できるか、プレビュー期間中の反応が注目される。
