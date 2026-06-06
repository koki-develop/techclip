---
date: "2026-06-07T02:31:15+09:00"
title: "自己複製ワーム「Miasma」がMicrosoft GitHubリポジトリ73件を侵害、AIコーディングエージェントを悪用したサプライチェーン攻撃"
description: "Miasmaワームが自動実行フックを悪用してClaude CodeやGemini CLIなどのAIコーディングエージェントを起動トリガーとし、MicrosoftのGitHub組織配下73リポジトリに拡散するサプライチェーン攻撃が確認された。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/miasma-worm-hits-73-microsoft-github.html"
  - "https://thenextweb.com/news/miasma-worm-microsoft-github-supply-chain"
  - "https://safedep.io/miasma-worm-ai-coding-agent-config-injection/"
---

## 攻撃の概要

2026年6月3日、自己複製型マルウェア「Miasma」がMicrosoftのGitHub組織（Azure、Azure-Samples、Microsoft、MicrosoftDocs）配下の73リポジトリに侵害をもたらした。GitHubは攻撃を検知した後、影響を受けたリポジトリへのアクセスを停止したと報告しており、封じ込めにかかった時間は「105秒以内」とされている。ただし、下流ユーザーの被害範囲は依然として不明確だ。

MiasmaはTeamPCPが2026年5月に公開した「Mini Shai-Hulud」の亜種であり、さらに遡れば2025年9月に登場したnpm初の自己複製マルウェア「Shai-Hulud」から続く一連のキャンペーンの最新段階にあたる。侵害されたリポジトリには、Azure Functions Host、Durable Taskエコシステム（.NET・Go・JS・MSSQL・Java実装）、azure-search-openai-demo、llm-fine-tuningなどの重要なインフラプロジェクトが含まれる。「durabletask」PyPIパッケージは2026年5月のTeamPCPによる侵害に続く再侵害であり、セキュリティアナリストのPaul McCarty氏は「同じリポジトリが先月のキャンペーンの起点となり今月の封じ込めの中心にもなっている。これは偶然ではない—同じ傷が再び開いたのだ」と指摘している。

## AIコーディングエージェントを標的にした注入メカニズム

今回の攻撃が注目を集めている最大の理由は、AIコーディングエージェントの自動実行機構を直接の起動トリガーとして利用した点にある。攻撃者は「chore: update dependencies [skip ci]」というコミットメッセージで6つのファイルをリポジトリに植え付けた。メインペイロードは `.github/setup.js`（4.3MBのランナー）で、これを以下の5つの開発ツールから自動起動するよう設定された。

- **Claude Code / Gemini CLI**：`.claude/settings.json` および `.gemini/settings.json` に `SessionStart` フックを追加し、`node .github/setup.js` を自動実行
- **Cursor**：`.cursor/rules/setup.mdc` に「always apply」ルールを設定し、AIアシスタントがセッション開始時に同コマンドを実行するよう誘導
- **VS Code**：`.vscode/tasks.json` に `folderOpen` トリガーを仕込み、フォルダを開くだけで実行
- **npm**：`package.json` の `test` スクリプトを上書き

この設計により、開発者が感染リポジトリをクローンしてエディタやAIエージェントで開くだけでペイロードが起動し、npmレジストリを一切経由せずにマルウェアを実行できる。

## ペイロードの技術詳細と自己複製機構

`.github/setup.js` 本体はキャラクタコード配列にシーザーシフト変換を施した難読化コードであり、`eval()` を経て実行される。復号後の非同期ローダーはAES-128-GCMで暗号化された2つのブロブを復号し、667KBのペイロードをランダムな一時ファイルに書き出してBunランタイム（ホスト環境になければ自動ダウンロード）で実行する。

最終ペイロードはAWS・Azure・GCP・Vault・Kubernetes・npm・GitHubの認証情報を収集する多機能窃取ツールだ。収集した認証情報を用いて被害者がアクセス可能なリポジトリに同様のコードをコミットすることで、エコシステム全体へと自律的に拡散する。GitHub検索では同一シグネチャを含むリポジトリが123件確認されており、攻撃者は「Miasma」系の命名パターンを持つ82件の公開リポジトリと「Hades - The End for the Damned」という命名パターンを持つ13件の公開リポジトリを使って盗んだ認証情報を保管・管理していた。

## 信頼モデルへの根本的な挑戦

セキュリティ企業FalconFeeds.ioはこの攻撃について「正当なキーで署名され、認証済みメンテナーが公開したパッケージは安全という仮定——プラットフォームが構築されてきた信頼モデルそのものを悪用している」と指摘した。

SafeDep社の研究者が強調するのは、AI開発ツールの普及が生み出した新たな脅威面だ。「クローンしたリポジトリをエディタで開くことは従来は安全と見なされていたが、AIコーディングエージェントの統合により危険な実行環境へと変わった」。Cursorのケースのように、設定ファイルの「always apply」ルールがAIアシスタント自身にスクリプト実行を指示するという手法は、AI固有の攻撃ベクタを示す前例となる。

検出インジケータとしては `.github/setup.js` の存在確認（`test -f .github/setup.js`）、署名のないコミット（`github-actions` 身元の利用）、AIエージェント設定ファイルへの不審なフックの追加が挙げられる。今回の攻撃はShai-Hulud登場からおよそ9カ月で急速に進化したサプライチェーン攻撃の最新形であり、AIコーディングツール統合が標準化しつつある開発環境において、リポジトリクローンという日常的な操作が新たなリスク要因となることを示した。
