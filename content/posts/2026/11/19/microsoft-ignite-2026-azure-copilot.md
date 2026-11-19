---
date: "2026-11-19T18:09:43+09:00"
title: "Microsoft Ignite 2026、新CPU「Azure Cobalt 200」とAI向けDB「HorizonDB」を一般提供、Copilotも自律エージェント化"
description: "MicrosoftはIgnite 2026でAzureの新CPUやデータベースを一般提供すると発表し、Copilotには自律的に動くエージェント機能やコード生成機能を追加した。"
tags:
  - Cloud
  - AI
  - OSS
references:
  - "https://azure.microsoft.com/en-us/blog/microsoft-ignite-2026-whats-new-in-azure-the-platform-purpose-built-for-ai/"
  - "https://www.microsoft.com/en-us/copilot/blog/2026/11/17/copilot-at-microsoft-ignite-expanding-whats-possible-with-intelligence-built-for-work/"
  - "https://github.blog/changelog/2026-11-17-github-copilot-in-jetbrains-ignite-releases/"
---

## 概要

Microsoftは11月17日、年次カンファレンス「Ignite 2026」でAzureプラットフォームとCopilotの両面にわたる大型発表を行った。インフラ側では新CPU「Azure Cobalt 200」とPostgreSQL互換データベース「Azure HorizonDB」が一般提供を開始し、エージェント主導のモダナイゼーション基盤「Azure Catalyst」も発表された。一方Copilot側では、ユーザーの指示を待たずに自律的にタスクを実行するエージェント「Autopilot」や、自然言語でアプリを作れる「Copilot Code」がロールアウトを始めている。developer向けにはGitHub CopilotのJetBrains対応も強化され、クラウドサンドボックスでのセッション実行やブラウザ操作連携が加わった。全体を通じて、Microsoftは「企業独自のコンテキスト(業務データやビジネスロジック)」をAI活用の競争優位性と位置づけ、インフラから開発者ツール、エンドユーザー向けアシスタントまで一体化した戦略を描いている。

## Azureインフラの刷新

「Azure Cobalt 200」は、前世代のCobalt 100 VM比で最大50%のCPU性能向上を実現したとされ、スケールアウト型のクラウドネイティブワークロードやエージェンティックAIワークロードを想定して設計された。MicrosoftはAzureにおいて自社開発のMaiaチップとNVIDIA・AMD製の最新チップを組み合わせることで、ワークロードごとに最適なシリコンを提供する戦略を進めている。データベース面では、PostgreSQL互換のフルマネージドサービス「Azure HorizonDB」が一般提供を開始した(Fabric向けの統合版「Fabric HorizonDB」はパブリックプレビュー)。ミリ秒レベルの低レイテンシに加え、ベクトル検索機能を標準搭載し、トランザクション処理・ベクトル検索・AI機能を1つのデータベースに統合する狙いがある。さらに、インフラ・アプリケーション・データの各レイヤーにまたがる近代化を支援する「Azure Catalyst」も発表され、発見・計画・移行・近代化・コードインテリジェンスを統合的に扱う。Microsoft SecurityやGitHub Copilotと連携し、近代化の過程で見つかった脆弱性の特定・修正までを一体的に行える点が特徴だ。

## Copilotの自律エージェント化

Copilot側の発表で最も注目されるのは、「Autopilot」と呼ばれる個人向けの自律エージェントだ。Teams や Outlook 上で常時稼働し、チャネルの監視やメールの追跡、定期作業の実行をユーザーからの明示的な指示なしに自律的に判断して行う。Microsoft Entra Agent IDを持つ独立したエンティティとして動作するため、IT管理者はアクセス権限の範囲設定やいつでものブロックが可能で、サインインや実行内容はすべて監査ログに記録される。発表では、サプライヤー審査プロセス全体(スケジュール作成からワークバック計画、会議実施、フォローアップ、ステークホルダーへの照会まで)を自動化する例が示された。もう一つの柱である「Copilot Code」は、自然言語で要件を説明するだけでアプリやダッシュボード、ウィジェットを作成できる機能で、近日一般提供予定。生成されたアプリはセキュアな「Copilot Managed Runtime」でテナント内にホストされ、Word文書と同様に組織内で共有できる。これらを支える基盤技術として「Work IQ」が挙げられており、Microsoft 365内の19.5エクサバイトに及ぶ分散データ(メール、Teams、Word、PowerPointなど)からタスクに関連する情報を識別する仕組みを持つ。また、品質・速度・コストのバランスを見ながらOpenAIやAnthropicなど複数モデルから最適なものを動的に選択する「Autoルーティング」も搭載されている。導入事例としては、Lillyで月5,000人以上がCopilot Coworkを利用し、Fortune 500企業の約80%がCoworkを導入していると紹介され、Clifford Chanceでの文書審査時間の大幅短縮やChevronでの大幅なコスト削減などの成果も挙げられた。

## 開発者向けツールの強化

開発者向けには、GitHub CopilotのJetBrains統合が強化された。新たに追加された「クラウドサンドボックス」は、GitHub がホストする分離環境でCopilotのセッションを実行できる機能で、ローカルマシンのリソースを消費せずにコード変更やテスト実行を並列に行える。また、JetBrains内で開始したセッションをVS CodeやCopilotアプリなど別のクライアントからも継続利用できるようになり、リモートの共有セッションを発見したり過去の履歴から再開したりできる。さらにChrome拡張機能と連携する「ブラウザ操作プラグイン」も追加され、Copilotがウェブページを開いて操作することが可能になった。これらの機能はいずれもパブリックプレビュー段階で、JetBrains側の設定から有効化する必要がある。

## 今後の見通し

Microsoftが示したコスト比較データ(GigaOmの2026年11月レポート、一般ユーザー向け・同等品質比較でCopilotはClaude比84%安価、ChatGPT比63%安価)は、エンタープライズAI市場における価格競争の激化を示唆している。Agent 365 Business Analyticsによる作業量の可視化や、定額制と使用量ベースを組み合わせたハイブリッド課金モデルの導入は、企業がAIエージェントの投資対効果を測定しやすくする狙いがある。インフラ(Cobalt 200、HorizonDB、Catalyst)からエンドユーザー向けエージェント(Autopilot、Copilot Code)、開発者ツール(GitHub Copilot for JetBrains)までを一体的に強化する今回の発表は、Microsoftが企業のAI導入における「全層戦略」をより明確に推し進めていることを表している。
