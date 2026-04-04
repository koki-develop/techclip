---
date: "2026-04-04T10:37:37+09:00"
title: "AWSがClaude CodeやCursorから直接サーバーレスアプリを管理できる「Agent Plugin for AWS Serverless」を発表"
description: "AWSはAIコーディングアシスタントと連携してサーバーレスアプリのビルド・デプロイ・管理を可能にする「Agent Plugin for AWS Serverless」をオープンソースで公開し、あわせてAWS Lambdaのファイルディスクリプタ上限を4倍の4,096に拡大した。"
tags:
  - Cloud
  - AI
references:
  - "https://aws.amazon.com/blogs/aws/aws-weekly-roundup-aws-ai-ml-scholars-program-agent-plugin-for-aws-serverless-and-more-march-30-2026/"
  - "https://aws.amazon.com/about-aws/whats-new/2026/03/agent-plugin-aws-serverless/"
  - "https://aws.amazon.com/blogs/developer/introducing-agent-plugins-for-aws/"
  - "https://aws.amazon.com/about-aws/whats-new/2026/03/aws-Lambda-file-descriptors-increase-4096/"
  - "https://github.com/awslabs/agent-plugins"
---

## 概要

AWSは2026年3月、AIコーディングアシスタントからサーバーレスアプリケーションのビルド・デプロイ・運用を一元管理できる「Agent Plugin for AWS Serverless」を発表した。Claude Code、Cursor、Kiroなどの主要AIコーディングツールに対応しており、開発者はチャット画面を離れることなくAWS Lambda関数の作成やAPIの設計・管理、インフラのプロビジョニングまでを実行できる。プラグインはAWSの公式GitHubリポジトリ（awslabs/agent-plugins）でオープンソースとして公開されている。

Claude Codeでは `/plugin install aws-serverless@claude-plugins-official` コマンドひとつでClaudeマーケットプレイスからインストールでき、個別スキルを選んで導入することも可能だ。

## 技術的な仕組みとスキル

Agent Pluginはスキル・サブエージェント・フック・Model Context Protocol（MCP）サーバーを1つのモジュールにまとめたオープンフォーマットの拡張機能で、複数のAIツール間で互換性を持つ設計となっている。開発ライフサイクル全体をカバーする主な機能は次のとおりだ。

- **Lambda関数の作成と管理**: Amazon EventBridge・Kinesis・AWS Step Functionsなどのイベントソースとの統合、可観測性・パフォーマンス最適化・トラブルシューティングのベストプラクティスを内包
- **IaCサポート**: AWS SAM（Serverless Application Model）とAWS CDKによる再利用可能なコンストラクト提供、CI/CDパイプラインとローカルテストへの対応
- **API設計**: Amazon API Gatewayを通じたREST API・HTTP API・WebSocket APIの設計と管理
- **ステートフルワークフロー**: Lambda Durable Functionsによるチェックポイント機構と高度なエラーハンドリング

## AWS Lambdaのファイルディスクリプタ上限も4倍に拡大

同時期に発表されたもう一つの重要な改善として、AWS LambdaのファイルディスクリプタUlimitが従来の1,024から4,096へ4倍に引き上げられた。この変更はLambda Managed Instances（LMI）上で動作する関数が対象で、LMIが同時に複数のリクエストを処理できる仕組み上、ファイルディスクリプタの枯渇がボトルネックになりやすいという課題を解消する。

ファイルディスクリプタはファイルのオープン・外部サービスへのネットワークソケット接続・並行I/Oストリームの管理など幅広い用途で消費されるため、I/O集中型ワークロードや大規模なコネクションプールを必要とするアプリケーション、マルチコンカレンシーを活用するサーバーレス設計において直接的な恩恵がある。本機能はLMIが一般提供（GA）されている全AWSリージョンで利用可能だ。

## 今後の展望

Agent Plugin for AWS Serverlessの登場は、AIコーディングアシスタントをインフラ管理の直接的なインターフェースとして位置づけるAWSの方向性を示している。オープンソースでの公開により、サードパーティによる拡張や他クラウドサービスとの連携プラグインの開発も期待される。Lambdaのファイルディスクリプタ拡大と合わせ、高スループット・高並行のサーバーレスアーキテクチャをAIドリブンな開発体験で構築しやすくなったといえる。
