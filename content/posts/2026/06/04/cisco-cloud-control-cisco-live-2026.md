---
date: "2026-06-04T03:30:34+09:00"
title: "CiscoがCisco Live 2026でAIエージェント統合運用基盤「Cisco Cloud Control」を発表、AgenticOps時代を宣言"
description: "CiscoはCisco Live 2026（ラスベガス）で、AIエージェントと人間が協調してITインフラを運用する統合クラウドプラットフォーム「Cisco Cloud Control」を発表し、量子耐性セキュリティや実行中インフラへの無停止パッチ適用など複数の新機能も披露した。"
tags:
  - Cloud
  - AI
references:
  - "https://newsroom.cisco.com/c/r/newsroom/en/us/a/y2026/m06/cisco-unveils-agentic-platform-for-operating-and-defending-critical-it-infrastructure.html"
  - "https://siliconangle.com/2026/06/02/ciscos-new-cloud-platform-aimed-securing-ai-infrastructure/"
  - "https://www.networkworld.com/article/4179673/cisco-brings-agentic-ops-platform-and-security-overhaul-to-cisco-live.html"
---

## 概要

Ciscoは2026年6月2日、ラスベガスで開催中のCisco Live 2026において、ネットワーク・セキュリティ・コンピュート・可観測性・コラボレーションを単一環境に統合したクラウドプラットフォーム「Cisco Cloud Control」を正式発表した。同社がこれを「AgenticOps」と呼ぶ新しいIT運用モデルの中核に据え、AIエージェントと人間の管理者が同じデータとインターフェースを通じて協調してインフラを運用するビジョンを示した。Cisco CPOのJeetu Patel氏は「AIエージェントはソフトウェアの速度で継続的に推論・行動し、重要インフラの拡張・管理・防御のあり方を根本から変える。ただしヒトは常に重要な判断の主導権を握り続ける」と述べた。同プラットフォームは2026年6月2日より米国での制御可用性(Controlled Availability)段階に入り、グローバル展開は追って予定している。

## Cisco Cloud Controlの主要機能

Cisco Cloud Controlは、複数の管理ダッシュボードを廃して単一の運用環境を提供する。バックエンドにはSplunk買収によって獲得したデータ基盤「Cisco Data Fabric」を活用し、クロスドメインのテレメトリーを一元的に集約・分析する設計だ。プラットフォームには開発ツールとして「Cloud Control Studio」が付属し、「Agent Builder」と「App Builder」を使って自然言語でカスタムエージェントやアプリケーションを構築できる。40以上のサードパーティプラットフォームとの統合に対応しており、既存の運用ツールチェーンとの連携も想定されている。

また「Cisco AI Canvas」と呼ばれる協調型ワークスペースが提供され、オペレータとAIエージェントがリアルタイムで問題の調査・対応にあたる。エージェントが実行するアクションはキューに積まれ、人間がその内容を確認・承認してから実行される仕組みで、人間の統制権を維持しながら自動化を進める設計思想が反映されている。Ciscoは40年分のネットワーク運用データで訓練した深層ネットワークモデルを組み込んでおり、異常検知や障害予測の精度向上に活かすとしている。

## セキュリティの強化：無停止パッチから量子耐性まで

セキュリティ面では複数の新機能が披露された。「Live Protect」は、脆弱性が発見されたタイミングで実行中のインフラに保護措置を適用するもので、再起動やアップグレードを伴わないのが最大の特徴だ。現時点ではNexus 9000シリーズスイッチで利用可能で、今後キャンパス・ブランチスイッチへも展開が予定されている。

量子コンピュータによる将来的な脅威への対策として「Quantum Ready Assessments」も発表された。「今採取、後復号化（Harvest Now, Decrypt Later）」型攻撃に対して最もリスクの高いアセットを特定する機能で、2026年7月にグローバル展開が予定されている。また新世代のルータ・スイッチ・ファイアウォールに量子耐性セキュアブートを標準搭載することも明らかにされた。

AIエージェント固有のセキュリティ課題に対応するため「DefenseClaw」も公開された。OpenAI CodexやClaude Codeなどローカルで動作するAIエージェントを対象に、脆弱性スキャンとアクセス制御を適用するフレームワークだ。さらに「Agentic IAM」としてAIエージェント向けのジャストインタイム・最小権限アクセス制御も提供され、担当者は「必要な瞬間に、必要な分だけのアクセス(just in time, just enough access)」と説明した。AIを活用したセキュリティ運用センター「Agentic SOC」も発表され、インシデント対応時間を従来の数時間〜数日から数分へと短縮することを目指す。

## その他の発表と今後の展望

Cisco Liveではその他にも、マルチクラウド環境間の接続を統一する「Cisco Multicloud Fabric」や新ハードウェア（C9550コアスイッチなど）が発表された。オンプレミス環境への対応として「Resilient Infrastructure Services」も拡張され、露出評価・基盤現代化・防御復元力の3段階のアプローチでフロンティアモデル脅威への対策を支援するとしている。

Ciscoは今回の発表全体を通じ、エンタープライズがAIチャットボットから自律型エージェントへとシフトする潮流に対して、インフラ層での主導権を確立する意図を明確にした。AgenticOpsというコンセプトは、単なるAI活用にとどまらず、人間とAIが対等に協働する新たな運用体制の確立を目指すものであり、今後のIT運用の方向性を占う重要な動きとして業界の注目を集めている。
