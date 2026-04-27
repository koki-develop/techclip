---
date: "2026-04-28T02:35:23+09:00"
title: "AWS、Bedrock AgentCore CLIを14リージョンで無償提供開始——CDK/TerraformによるAIエージェントのIaC管理が可能に"
description: "AWSがBedrock AgentCore CLIを14リージョンで無償提供開始し、CDKやTerraformを使ったAIエージェントのインフラコード管理を実現した。"
tags:
  - Cloud
  - AI
references:
  - "https://aws.amazon.com/blogs/aws/aws-weekly-roundup-anthropic-meta-partnership-aws-lambda-s3-files-amazon-bedrock-agentcore-cli-and-more-april-27-2026/"
---

## Amazon Bedrock AgentCore CLI の概要

AWSは2026年4月27日付けのWeekly Roundupにて、**Amazon Bedrock AgentCore CLI**の提供開始を発表した。このCLIは14のAWSリージョンで追加料金なしで利用でき、AIエージェントをインフラコード（IaC）として管理するための開発者向け機能を提供する。

AgentCoreには2つの主要な機能が含まれる。「Managed Harness（プレビュー）」は、モデル・システムプロンプト・ツールを指定するだけでエージェントをすぐに実行できる仕組みで、オーケストレーションコードを自前で書く必要がない。「AgentCore CLI」はIaCガバナンスのもとでエージェントをデプロイするためのツールで、**AWS CDKへの対応は即日、Terraformサポートも近日対応予定**とされている。また、ハーネスのオーケストレーション部分を**Strandsベースのコード**としてエクスポートする機能も備えており、必要に応じてフルコントロールへ移行できる柔軟性も持つ。

## AWS LambdaとS3 Filesの統合

同週のアップデートでは、**AWS LambdaがAmazon S3バケットをファイルシステムとしてマウントできる**新機能「S3 Files」も発表された。従来のように事前にデータをダウンロードする必要がなく、Amazon EFSのインフラを基盤としているためS3のスケーラビリティ・耐久性・コスト効率をそのまま享受できる。複数のLambda関数が同一ファイルシステムに同時アクセスできるため、**AIエージェントがメモリを永続化するワークロード**など、機械学習系のユースケースで特に有効とされている。

## AnthropicおよびMetaとのパートナーシップ拡大

パートナーシップ面では2件の大型発表があった。Anthropicとの協業深化として、**ClaudeモデルがAWS TrainiumおよびGravitonインフラ上でトレーニング**されることが明らかになった。また、チームベースのエンタープライズワークフロー向けの「Claude Cowork」がAmazon Bedrockで利用可能になり、統合された開発体験を提供する「Claude Platform on AWS」も近日公開予定とされている。

Metaとの合意では、MetaがAWS Gravitonプロセッサーを大規模導入し、リアルタイム推論やコード生成を含むエージェント型AIワークロードに**数千万コア規模のGraviton**を活用することが発表された。

## その他の主要アップデート

その他のAWSアップデートとして、**Aurora Serverless**がスケーリングアルゴリズムの改善により最大30%のパフォーマンス向上を達成したほか、**EKS Hybrid Nodes Gateway**がクラウドとオンプレミスのKubernetes環境間のネットワーキングを追加コストなしで自動化する機能を提供開始した。また、**Bedrock Cost Attribution**として、AIワークロードのコストを細かくタグ付け・追跡できるコスト可視化機能も追加されている。これらの発表全体を通じて、AIエージェントの本番デプロイ基盤整備が急速に進んでいることが見て取れる。
