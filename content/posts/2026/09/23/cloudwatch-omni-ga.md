---
date: "2026-09-23T18:14:31+09:00"
title: "AWS、生成AI・エージェント向け可観測性サービス「Amazon CloudWatch Omni」を一般提供開始"
description: "AWSがIDE統合や17種類の評価指標を備えた生成AI・エージェントワークロード向け可観測性サービス「Amazon CloudWatch Omni」の一般提供を開始した。"
tags:
  - Cloud
  - AI
references:
  - "https://aws.amazon.com/blogs/aws/introducing-amazon-cloudwatch-omni-ai-powered-observability-for-generative-ai-and-agentic-workloads/"
---

## 概要

AWSは9月22日、生成AIおよびエージェント型ワークロード向けの新しい統合可観測性サービス「Amazon CloudWatch Omni」の一般提供を開始した。エージェント型AIは非決定的な振る舞いをするため、レイテンシやエラー率といった従来型のモニタリング指標だけでは応答品質の劣化を検知できないという課題があった。CloudWatch Omniはこの課題に対応するため、開発者がローカルのIDEで直接トレースを確認できる層と、オペレータが専用のWeb UIで本番環境を監視する層の二層構造を採用している。

## 主な機能

開発体験の中心となるのがIDE統合で、VS CodeとKiro向けにネイティブ拡張機能を提供する。コマンドパレット(Command + Shift + P)からプロジェクトを作成でき、AWSアカウントがなくても無料で使い始められる点が特徴だ。実際にBedrockを利用する段階になって初めて認証情報が必要になる。トレース機能では、LLM呼び出しやツール実行、推論といったエージェントの各ステップを階層的なタイムラインとして記録し、比較モードで異なるプロンプト間の挙動差を並べて検証できる。評価面では、一貫性(Coherence)、有用性(Helpfulness)、忠実性(Faithfulness)、ルーティング正確性(Routing correctness)などを含む17種類の組み込み評価器を搭載し、従来の指標では見逃されがちな品質低下を捕捉する。さらにプレイグラウンド・実験機能では、異なるシステムプロンプトやモデル構成をリアルタイムで比較テストでき、実験ビューでは同一データセットに対する複数エージェントのスコア、レイテンシ、トークン使用量を並列評価できる。

## 対応フレームワークと標準

CloudWatch OmniはLangChain、LangGraph、CrewAI、OpenAI SDK、Strands、Vercel AI SDK、Amazon Bedrock AgentCoreに対応し、PythonとTypeScriptの両方をサポートする。計装にはOpenInferenceとAWS Distro for OpenTelemetry(ADOT)という標準規格を採用しており、これにより、Lambda、ECS、EKSなど複数のデプロイ環境で既に計装・利用可能な設計となっている。プロンプトのバージョン管理、回帰テスト、マルチターン会話の分析、エージェントアーキテクチャの可視化といった用途を想定している。

## 今後の展望

AWSのブログ記事はDaniel Abib氏の執筆によるもので、まずは開発時点でのデバッグ体験向上に焦点を当てたIDE拡張機能を無料で提供することで、エージェント開発者への浸透を図る狙いがうかがえる。OpenInferenceやADOTといったオープンな計装標準を採用したことで、特定のフレームワークやデプロイ環境に縛られない可観測性基盤としての拡張が見込まれる。生成AIアプリケーションの本番運用が広がる中、非決定的な出力品質を継続的に監視・評価する仕組みへの需要は今後さらに高まるとみられ、CloudWatch Omniはその中核ツールの一つとなる可能性がある。
