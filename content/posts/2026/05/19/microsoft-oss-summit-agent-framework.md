---
date: "2026-05-19T02:44:58+09:00"
title: "MicrosoftがOSS Summit NA 2026でマルチエージェントSDK「Microsoft Agent Framework」とAzure Container Linux GAを発表"
description: "Microsoftはミネアポリスで開催中のOpen Source Summit NA 2026にて、マルチエージェントシステム構築用SDKの「Microsoft Agent Framework」、AIエージェント向けガバナンスツール「Agent Governance Toolkit」、コンテナ最適化OS「Azure Container Linux」のGA開始を発表した。"
tags:
  - OSS
  - Cloud
references:
  - "https://opensource.microsoft.com/blog/2026/05/18/from-open-source-to-agentic-systems-microsoft-at-open-source-summit-north-america-2026/"
  - "https://www.linuxfoundation.org/press/open-source-summit-north-america-2026-schedule-showcases-next-era-of-ai"
---

## 概要

ミネソタ州ミネアポリスで2026年5月18〜20日に開催中のOpen Source Summit North America 2026（OSS NA 2026）にて、MicrosoftはAIエージェント分野における複数のオープンソースイニシアティブを発表した。MicrosoftのAzure OSS担当コーポレートバイスプレジデントであるBrendan Burns氏は「オープンソースはAIの基盤だ」と述べ、同社がクラウドネイティブから「AIネイティブ」への移行を次世代の進化と位置づけていることを強調した。AIがissueトリアージ・テスト・コードレビューといった開発プロセス自体を自動化することで、オープンソース開発そのものを再構築するビジョンも示された。

## Microsoft Agent Framework とエージェント基盤スタック

Microsoftが発表した「Microsoft Agent Framework」は、マルチエージェントシステムの構築・展開を支援するOSSのSDKだ。同社はこれを「オープンなエージェントスタック」の中核と位置づけており、RayおよびNVIDIA Dynamoとのパートナーシップによるクロスフレームワーク連携、ベンダー中立のエージェント通信標準「A2A Protocol」も合わせて整備している。さらに「Agent Governance Toolkit」では、AIエージェントにID管理・ポリシー適用・監査ログといったOSレベルのガバナンス機能を付与し、企業のコンプライアンス要件に対応できる設計となっている。Linux Foundationが主導する「Agentic AI Foundation（AAIF）」はLinux Foundation史上最速で成長しているプロジェクトと認められており、Microsoftも積極的に貢献している。

## Azure Container Linux と Azure Linux 4.0

インフラ面では、コンテナ最適化不変OS「Azure Container Linux」のGA（一般提供開始）も発表された。Azure Linux 4.0はAzure仮想マシン向けパブリックプレビューに入り、Microsoft Build（6月2日）でより広範なロールアウトが予定されている。いずれも削減されたパッケージフットプリントと透明性の高いサプライチェーンを特徴とし、攻撃対象領域を最小化することで規制対応ワークロードにも適した設計となっている。ホスト環境からコンテナまで一貫したパフォーマンスを実現し、Azureオペレーションチームによるメンテナンスとアップストリームへの継続的な貢献も維持される。

## オープンソースセキュリティへの投資と業界動向

セキュリティ面では、OpenSSF/Alpha-Omegaへの複数フェーズにわたる資金提供と、GitHubが運営する「GitHub Secure Open Source Fund」（プロジェクトあたり1万ドルの支援＋メンターシップ）への継続的な関与も明らかにされた。MicrosoftのAzureはCNCFプロジェクトへの最大のパブリッククラウドコントリビューターとして3年連続でランク付けされており、オープンソースエコシステム全体への貢献をさらに拡大している。OSS NA 2026ではMicrosoftのほか、OpenAI・Intel・IBM ResearchもSBOMの運用化やAIサプライチェーン保護、エッジ・IoT向けLinux最適化など多様なセッションに参加しており、業界全体でのAI時代のオープンソース基盤強化に向けた動きが活発化している。
