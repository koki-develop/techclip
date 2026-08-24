---
date: "2026-08-24T20:06:58+09:00"
title: "GoogleのAIエージェント通信規格「A2A」、Linux Foundation傘下のAgentic AI Foundationへ正式移管"
description: "GoogleがAIエージェント間通信プロトコル「A2A」をAgentic AI Foundationに寄贈し、AnthropicのMCPと並ぶベンダー中立の業界標準としての地位を固めた。"
tags:
  - AI
references:
  - "https://www.axios.com/2026/08/17/a2a-agentic-ai-foundation-open-ai-standards"
  - "https://www.techzine.eu/news/devops/143659/google-transfers-a2a-to-the-agentic-ai-foundation/"
  - "https://techstrong.ai/articles/google-moves-a2a-under-agentic-ai-foundation/"
---

## 概要

GoogleはAIエージェント間の通信を標準化するプロトコル「Agent2Agent（A2A）」を、Linux Foundation傘下の新団体「Agentic AI Foundation（AAIF）」に正式に寄贈した。A2Aはもともと2025年4月にGoogleが立ち上げたプロジェクトで、同年6月にはすでにLinux Foundationへ移管されていたが、今回はさらに一歩進み、AnthropicのModel Context Protocol（MCP）やOpenAIのAGENTS.mdといった競合・関連規格と同じAAIFの傘下に置かれることになった。異なるベンダーが提供するAIエージェント同士が、共通の中立的なガバナンスのもとで相互運用できる基盤を整える動きとして注目されている。

## 技術的な詳細

A2Aは、異なるフレームワークやベンダーで構築されたAIエージェント同士が互いを発見し、通信し、タスクを委任し合うための仕組みを提供する。各エージェントは自身の機能や接続方法を記述した「エージェントカード」を公開し、他のエージェントがそれを読み取ることで能力を把握できる。今年3月にリリースされたバージョン1.0では、マルチテナンシー対応やバージョンネゴシエーション、暗号署名によって身元を検証できる「署名付きエージェントカード」といった機能が追加され、実運用に耐える堅牢性が強化された。

A2Aが担うのは主にエージェント同士の相互通信であるのに対し、MCPはエージェントと外部ツール・データソースとの接続を標準化する役割を担う。両者は補完関係にあり、大規模なマルチエージェントシステムを構築する上で不可欠なインフラの両輪と位置づけられている。

## 導入状況と業界の反応

A2Aにはすでに150以上の組織が支援を表明しており、Atlassian、Box、Intuit、LangChainといったソフトウェア企業に加え、AccentureやDeloitteなどのコンサルティング大手も名を連ねる。実運用の例としては、サプライチェーンや金融サービス、モバイルプラットフォーム領域での採用が進んでおり、Huaweiは音声アシスタント「Celia」の連携にA2Aを活用しているほか、TencentのWeChatも他社製OEMアシスタントとの統合に利用している。Google Cloud、Microsoft Azure、AWSといった主要クラウドベンダーも対応を進めており、商取引向けの拡張プロトコル「AP2（Agent Payments Protocol）」の開発も並行して進んでいる。AAIFの運営は、戦略・予算・会員ポリシーを担う統治委員会と、プロジェクト承認を担当する技術委員会の二層構造で行われる。

## 今後の展望

Googleはこのオープン標準アプローチを「Androidのような」エコシステム戦略になぞらえており、AAIFという中立的な傘のもとでA2Aの採用をさらに広げたい考えだ。断片化しがちなエージェント間相互運用性の環境が、業界横断の標準化によって統合されることへの期待は大きい。一方で、SeekrのリードAIソリューションアーキテクトを務めるMahesh Shanmugasundaram氏は、エージェント同士が連鎖的にタスクを委任していく過程で「各参加者が前段のエージェントの誤りをそのまま信頼して増幅してしまう可能性」を懸念点として指摘している。小さな誤りが連鎖の中で高い確信度を伴う誤った結論へと変質しかねないため、通信手順の標準化だけでなく、検証可能なメタデータやトレーサビリティの仕組みを合わせて整備することが今後の課題となりそうだ。
