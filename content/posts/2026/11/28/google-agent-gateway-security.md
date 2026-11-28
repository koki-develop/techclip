---
date: "2026-11-28T18:08:28+09:00"
title: "Google、AIエージェント専用の統一セキュリティ基盤「Agent Gateway」とWorkspace MCPサーバーを一般提供開始"
description: "Googleが企業向けAIエージェントを安全に運用するための「Google Cloud Agent Gateway」とGoogle Workspace MCPサーバー・CLIを一般提供し、2027年2月からの新インターフェース移行義務化を発表した。"
tags:
  - Cloud
  - AI
  - Security
references:
  - "https://cloud.google.com/blog/products/identity-security/deploying-agents-safely-in-your-enterprise"
---

## 概要

Googleは11月24日、企業内で拡大するAIエージェント利用を安全に管理するための新たなセキュリティ基盤を発表した。中核となるのは、LLM・MCP・Agent2Agent（A2A）トラフィックに対応したプロトコルネイティブなゲートウェイ「Google Cloud Agent Gateway」と、Gmail・Drive・Docs・Sheets・Slides・Calendar・Chat・Tasksなど主要Workspaceサービスに対応する「Google Workspace MCPサーバー」および「Workspace CLI」の一般提供（GA）である。背景には、従来型の人間向けREST APIとOAuthトークンによる認可モデルが、機械速度で自律的に行動するAIエージェントのリスクに対応できないという課題認識がある。Googleによれば、Workspaceは月間2.8兆件のAPIコールを処理し、Drive APIのトラフィックは2022年比で2.5倍、1日あたりのDrive読み取りは180億件以上に達しており、この規模でエージェントが人間の確認を介さずに行動する以上、トークンの有効性確認だけでは不十分だとしている。

## Agent GatewayとWorkspace MCP/CLIが提供する機能

Agent Gatewayは、Agent RegistryにおけるAgent Identityの検証、IAMポリシーの強制、デフォルト拒否の送信ルール、そしてプロンプトインジェクション対策サービス「Model Armor」によるリクエスト検査を提供する。一方、Workspace MCPサーバーは専用のリモートサーバーとしてパーミッション確認とDLP（データ損失防止）チェックを内蔵し、メール送信やDrive共有権限の変更といった影響度の高い操作では人間による承認（Human-in-the-loop）を求める設計になっている。非エージェント向けのOAuthクライアントからのアクセスは拒否される。Workspace CLIはローカルエージェントやターミナルワークフロー向けに構造化JSON出力とスコープ付きOAuthサインインを提供する。両者とも、エージェントには従来の人やアプリとは区別された専用のOAuthクライアントIDないしAgent Identityが割り当てられ、共有キーや長期キーを使わない最小権限のアクセスが可能になる。

## 統一的なセキュリティ制御と2027年の義務化

Googleはこれらの基盤の上に、ポリシーチェック、エージェント専用ID、高影響度アクション時の人的承認、可視性と取り消し、機密データの境界設定、データ利用ルールという6つの統一的なセキュリティ制御を整備するとしている。特に注目すべきは、新たな「Workspace AI Tools Addendum」により、AIエージェントは今後Workspace REST APIを直接呼び出すのではなく、Workspace MCPサーバーまたはCLIの利用が義務付けられる点だ。技術的な強制は2027年2月1日から開始され、移行のための準備期間が設けられている。また同Addendumでは、生データの永続保存やモデル学習への利用、派生データの長期保持、API経由のスクレイピングを禁止し、定義された期間内の削除やユーザー切断時のデータ削除を求めるなど、データ利用に関する厳格なルールも定められた。Workspaceエージェントの利用量に対する課金は2027年4月1日から開始される予定である。

## 企業への影響と今後の展望

今回の発表は、AIエージェントが情報を「読む」存在から自律的に「行動する」存在へと変わる中で、セキュリティモデルをリクエストパスそのものに組み込む必要があるというGoogleの問題意識を反映している。企業にとっては、Security Command CenterやAgent Observability、Cloud Audit Logsとの連携によりエージェントの活動を可視化・監査・取り消しできるようになる一方、2027年2月の義務化に向けてMCPサーバーやCLIへの切り替え、人的承認フローの実装、Model Armorによるプロンプトインジェクション対策などの準備が必要になる。GoogleはすでにWorkspaceにおいてスパム・フィッシング・マルウェアの99.9%以上を検出しているとしており、今回の施策はこうした既存の防御網にエージェント特有のリスク管理を上乗せする形だ。40億ユーザー、1,300万組織という規模を抱えるWorkspaceにおいて、AIエージェントの安全な運用がどこまで実効性を持つかは、今後の企業導入の広がりとともに検証されていくことになる。
