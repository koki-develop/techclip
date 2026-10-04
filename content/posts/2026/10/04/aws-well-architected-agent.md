---
date: "2026-10-04T19:56:55+09:00"
title: "AWS、クラウド環境を自律分析するAIエージェント「Well-Architected Agent」をプレビュー公開"
description: "AWSはWell-Architected Frameworkの4つの柱に基づきクラウド環境を自動分析し最適化提案を行うAIエージェント「Well-Architected Agent」のパブリックプレビューを発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://aws.amazon.com/blogs/aws/announcing-aws-well-architected-agent-an-ai-powered-intelligence-to-optimize-your-cloud-environment-preview"
---

## 概要

AWSは10月1日、クラウド環境のコスト・セキュリティ・パフォーマンス・耐障害性を自律的に分析し、改善策を提案するAI駆動エージェント「AWS Well-Architected Agent」のパブリックプレビューを発表した。従来の「AWS Well-Architected Tool」が利用者自身による手動のセルフレビューを前提としていたのに対し、新エージェントはAWS Well-Architected Frameworkの原則に基づきながら、65以上のAWSサービスにまたがる利用率メトリクス、リソース構成、アプリケーショントポロジーを自動的に相関分析し、継続的にレコメンデーションを生成する点が特徴だ。

## 主な機能

Well-Architected Agentは大きく3つの機能で構成される。第一に、個々のベストプラクティス違反を指摘するだけでなく、ユーザーが設定したビジネス目標に沿って提案に優先順位を付ける「目標軸のインテリジェンス」。第二に、単一リソースの修正提案、複数リソースをまとめた統合的な改善提案、さらにアーキテクチャパターンレベルの提案という3段階のレコメンデーションを提供する仕組み。第三に、提示された改善策をAWSマネジメントコンソール、Infrastructure as Code(Terraform、CloudFormation、CDKなど)、CLIコマンドのいずれの形式でも適用できる柔軟な復旧オプションだ。IaC対応により、本番デプロイ前のアーキテクチャレビューにも活用できる。

利用を開始するには、AWS Well-Architectedコンソールでエージェントプロファイルを作成し、IAMロールを設定、分析対象のアプリケーションコンテキストを追加する。設定完了から24時間以内に初回のレコメンデーションが生成されるという。なお利用にはAWS Supportプランへの加入が必須となる。

## 提供状況と既存ツールとの関係

プレビュー版は現時点でUS East (N. Virginia)、US East (Ohio)、US West (Oregon)の3リージョンで利用可能だが、分析対象となるワークロード自体はすべてのAWSコマーシャルリージョンから登録できる。価格については発表時点で明示されていない。

既存のAWS Well-Architected Toolは廃止されるわけではなく、ユーザー定義レンズによる独自基準での手動評価ツールとして引き続き提供される。AWSは今回のエージェントによる提案がAI生成であるため誤りや不完全な情報を含む可能性があるとし、適用前の利用者自身による評価・検証を推奨している。クラウド運用の継続的な最適化を自動化へと進める動きとして、今後の機能拡充や対応リージョンの拡大が注目される。
