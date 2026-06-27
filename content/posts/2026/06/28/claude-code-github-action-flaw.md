---
date: "2026-06-28T02:28:19+09:00"
title: "Claude Code GitHub Actionの脆弱性、Issueを1件投稿するだけでリポジトリを完全掌握できるサプライチェーンリスク"
description: "GMO Flatt SecurityのRyotaKがClaude Code GitHub Actionに権限バイパスとプロンプトインジェクションを組み合わせた脆弱性を発見し、悪意あるIssue1件でAnthropic自身のリポジトリを含む任意のリポジトリを乗っ取れることが明らかになった。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/06/claude-code-github-action-flaw-let-one.html"
  - "https://flatt.tech/research/posts/poisoning-claude-code-one-github-issue-to-break-the-supply-chain/"
  - "https://cybersecuritynews.com/claude-codes-github-actions-vulnerability/"
  - "https://www.microsoft.com/en-us/security/blog/2026/06/05/securing-ci-cd-in-agentic-world-claude-code-github-action-case/"
  - "https://www.esecurityplanet.com/threats/claude-code-github-actions-flaw-created-supply-chain-attack-risk/"
---

## 概要

GMO Flatt SecurityのセキュリティリサーチャーRyotaKは、AnthropicのClaude Code GitHub Actionに重大な脆弱性を発見した。悪意あるGitHub IssueをターゲットのリポジトリにポストするだけでCI/CDワークフローを乗っ取れるというもので、Anthropicのアクション本体のリポジトリ（`anthropics/claude-code-action`）が侵害されれば、それを利用するすべてのダウンストリームプロジェクトへのサプライチェーン攻撃に発展しうる深刻なリスクだった。脆弱性はCVSS v4.0スコア7.8と評価され、Anthropicは報告から4日以内に初期修正を施した。

## 脆弱性の技術的詳細

今回の攻撃は2種類の脆弱性を連鎖させることで成立する。

**権限バイパス（GitHub App Permission Bypass）**：Claude Code GitHub Actionの`checkWritePermissions()`関数は、名前が`[bot]`で終わるアクターを実際の権限にかかわらず無条件に許可していた。GitHub Appは公開リポジトリに対して暗黙の読み取りアクセスを持ち、インストールトークンを使って任意の公開リポジトリにIssueやPull Requestを作成できる。これにより、攻撃者は自身のリポジトリに悪意あるGitHub Appを作成・インストールし、そのインストールトークンを用いてターゲットリポジトリでIssueを開くだけで、権限チェックを完全に迂回できた。

**プロンプトインジェクション**：権限バイパスに成功した後、攻撃者はIssueの説明文に偽のエラーメッセージや指示を埋め込み、Claude Codeに任意のコマンドを実行させることができた。Claude CodeはBashコマンドの一部（`cat`、`head`など）をユーザー承認なしに実行するため、Linuxの擬似ファイル`/proc/self/environ`を読み取ることでワークフロープロセスのすべての環境変数を外部に送信できた。

## 漏洩する情報とサプライチェーンへの影響

`/proc/self/environ`から取得できる最も重大な情報は`ACTIONS_ID_TOKEN_REQUEST_TOKEN`と`ACTIONS_ID_TOKEN_REQUEST_URL`だ。これらを使ってGitHub ActionsのOIDCトークン交換プロセスを再現することで、ターゲットリポジトリへのインストールトークンを取得でき、リポジトリコンテンツ・Issue・PR・ディスカッション・ワークフローファイルへの書き込みアクセスが手に入る。

さらに深刻なのは、Anthropicが管理する`anthropics/claude-code-action`リポジトリ自体も同じワークフローを使用していた点だ。このリポジトリへの侵害に成功すれば、アクションに悪意あるコードを仕込んでアップストリームに反映させ、Claude Code GitHub Actionを利用するすべてのプロジェクトを一括して攻撃できるサプライチェーン攻撃が成立する。

また、デフォルトのワークフロー設定が`allowed_non_write_users: "*"`（誰でもトリガー可能）になっていたことや、2段階のワークフローチェーンを悪用してIssueへの`write`権限を持つトークンを先に窃取し、それを使って信頼済みユーザーの処理前にIssueを編集してプロンプトインジェクションペイロードを注入するという高度な攻撃経路も報告されている。

## 修正タイムラインと推奨対策

RyotaKが2026年1月12日に脆弱性を報告し、Anthropicは1月16日（4日後）にGitHub Appをデフォルトで拒否する修正をコミットした。その後も春にかけて多層的なハードニングが続けられ、現在の修正済みバージョンは**claude-code-action v1.0.94**となっている。主な追加対策として、人間アクターの検証（`checkHumanActor()`）、ワークフロー実行サマリーセクションのデフォルト無効化、URLベースの情報漏洩をブロックするカスタム`gh`コマンドラッパー、子プロセスへの環境変数のスクラビング、トリガー後に編集されたIssueやコメントを無視するロジックが実装されている。バグバウンティ報酬は基本額$3,800に追加バイパス発見のボーナス$1,000を加えた合計$4,800が支払われた。

Claude Code GitHub Actionを利用している組織は、`allowed_non_write_users`の設定を見直し、ワークフローに公開するシークレットをAnthropicのAPIキーと`GITHUB_TOKEN`のみに絞り込み、可能であればワークフローのトリガーを信頼済みユーザーに限定することが推奨される。本件はAIコーディングツールをCI/CDパイプラインに統合する際のプロンプトインジェクション対策と最小権限原則の重要性を改めて示す事例となった。
