---
date: "2026-08-11T20:14:06+09:00"
title: "Amazon・Microsoft・OpenAI・Vercel・Cursorら、AIエージェント拡張機能の可搬パッケージ規格「Agent Plugins 1.0.0」を共同発表"
description: "Amazon・Microsoft・OpenAI・Vercel・Cursorらがスキルやツールをクライアント横断で配布できるオープン規格「Agent Plugins 1.0.0」を発表し、Googleもコアメンテナーとして参加した。"
tags:
  - AI
  - OSS
references:
  - "https://developers.googleblog.com/agent-plugins-package-your-skills-tools-and-more/"
  - "https://vercel.com/blog/introducing-agent-plugins"
  - "https://aws.amazon.com/blogs/opensource/aws-supports-agent-plugins-an-open-standard-for-portable-agent-extensions/"
---

## 概要

Amazon（AWS）、Microsoft、OpenAI、Vercel、Cursorは2026年8月6日、AIエージェント向けの拡張機能を統一フォーマットでパッケージ化するベンダー中立のオープン規格「Agent Plugins 1.0.0」を共同で発表した。開発者が「Agent Skills」（エージェントへの指示やリソース）や「MCPサーバー」（外部ツール・データへの接続）を一度パッケージ化するだけで、VS Code、GitHub Copilot、Cursor、ChatGPT/Codex、Kiroなど複数のクライアントに配布できるようにすることが狙いだ。発表と同時にGoogleもコアメンテナーとして参加を表明し、Agents CLIとData Agent Kitの2製品で早速サポートを開始している。技術統括委員会にはAWS、Cursor、Microsoft、OpenAI、Vercelが創立メンバーとして名を連ねる。

## 背景となった課題

従来、AIエージェント向けのスキルやツール定義は、クライアントごとにマニフェスト形式や配置ルールが異なっていた。そのため開発者は同じ機能を複数のクライアント仕様に合わせて個別に作り直したり、フォークして維持管理したりする必要があり、時間を浪費していたという。各社のブログ記事は、この状況をJavaScriptエコシステムにおける`package.json`や、コンテナの世界におけるOCI標準フォーマットの登場になぞらえ、「共通の標準があれば手作業による重複対応を減らせる」という歴史的パターンを踏まえた取り組みだと説明している。

## 技術的な仕組み

Agent Pluginsの基本単位は、固定されたディレクトリ構造を持つプラグインパッケージだ。具体的には以下の要素で構成される。

- `plugin.json` — スキーマバージョンやプラグイン名など最小限のメタデータのみを持つマニフェスト
- `skills/` ディレクトリ — Agent Skillsコンポーネントを格納するサブディレクトリ
- `mcp.json` — MCPサーバーの設定を定義するファイル
- クライアント固有の拡張領域（例: `com.example.client/`）— 各クライアントが独自機能を追加できる名前空間

互換クライアントはこの固定ロケーションをスキャンしてコンポーネントを自動検出する。仕様は「発見と検証は独立して行われ、不正なコンポーネントが他のコンポーネントに影響しない」設計になっており、"restraint is the point"（抑制すること自体が狙い）という設計哲学のもと、相互運用に必須の要素だけを標準化している。逆に、インストール機構、配布プロトコル、権限モデル、サンドボックス化、トラスト検証といった要素は意図的に仕様の対象外とされ、各クライアントが独自に差別化できる余地として残されている。

なお、Agent Pluginsはより広いエコシステムの一層に過ぎない。リソース発見プロトコルである「ARD（Agentic Resource Discovery）」、リソース説明形式の「AI Catalog」、パッケージングを担う「Agent Plugins」、実行基盤である「MCP/Agent Skills」という独立した複数レイヤーで構成され、各レイヤーは個別に採用することも可能だという。

## 対応ツールと実装状況

発表時点でChatGPT/Codex、Cursor、GitHub Copilot、Kiro、VS Codeが既にAgent Pluginsに対応している。Kiroは、specやhook、自動テストなどの仕組みで開発ライフサイクル全体にわたりエージェントを開発者の意図に沿わせる「エージェントハーネス」であり、その拡張機能である「Kiro Powers」を通じてプラグインをサポートし、AWSはLambda、S3、DynamoDBなど30以上のキュレートされたスキルを含む「AWS Agent Toolkit」を提供する。Googleも参加表明と同時に、エージェントの構築・評価・デプロイ向けスキルを提供する「Agents CLI」と、BigQueryなどGoogle Cloudのデータサービスと連携する「Data Agent Kit」の2製品でサポートを開始した。

## 今後の展望

現行のバージョン1.0.0はAgent SkillsとMCPサーバーの2種類のみを標準化の対象としているが、技術統括委員会はフック（hooks）やサブエージェント（sub-agents)など新たなコンポーネント型の追加を、技術的な収束状況や実際のニーズを見ながら検討していく方針だ。AWSはブログの中で、モデル選択における脱ベンダーロックインの流れと同様に、ツール選択においてもベンダーロックインを避ける狙いがあると位置づけており、Model Context Protocol（MCP）やAgent Client Protocol、x402など他のオープン標準への投資も引き続き進めていくとしている。
