---
date: "2026-04-13T02:16:50+09:00"
title: "Azure MCP Server 2.0安定版リリース、57サービス276ツールでAIエージェント自動化を強化"
description: "MicrosoftがAzure MCP Server 2.0の安定版をリリースし、57のAzureサービスにわたる276のMCPツールを提供するとともに、セルフホストリモートサーバー機能やセキュリティ強化を実現した。"
tags:
  - OSS
  - Cloud
references:
  - "https://devblogs.microsoft.com/azure-sdk/announcing-azure-mcp-server-2-0-stable-release/"
  - "https://www.c-sharpcorner.com/news/microsoft-announces-azure-mcp-server-20-stable-release-for-enterprise-ai-automation"
---

## 概要

Microsoftは2026年4月10日、Azure MCP Server 2.0の安定版リリースを発表した。Model Context Protocol（MCP）仕様を実装したこのサーバーは、AIエージェントがAzureリソースと標準化されたツールを通じてやり取りできる基盤を提供する。今回のバージョン2.0では、57のAzureサービスにわたる276のMCPツールが揃い、プロビジョニングから診断までのエンドツーエンドの運用シナリオに対応する。VS Code、Visual Studio、IntelliJ、Eclipse、CursorといったIDEや、GitHub CopilotなどのCLIツールとの統合も可能で、エンタープライズ向けAI自動化の基盤として活用できる。

## セルフホスト対応と主要機能

バージョン2.0の中核となる新機能は、セルフホスト型リモートサーバー機能だ。これにより、チームが自社環境にサーバーをデプロイし、一貫したポリシーとセキュリティ制御のもとで集中管理できるようになる。エンタープライズ環境での採用を想定し、HTTPベースのリモートホスティングが強化されている。

認証面では、マネージドIDによるデプロイメントに加え、OpenID Connectデリゲーションを用いたOn-Behalf-Of（OBO）フローが利用可能になった。これにより、サインイン済みユーザーのコンテキストで安全にAzure APIを呼び出せる。また、複数のツールセットを使用するシナリオでの信頼性を高めるパフォーマンス向上や、コンテナイメージサイズの削減によるコンテナデプロイの効率化も図られている。

## セキュリティとコンプライアンス対応

セキュリティ面では、エンドポイント検証の強化と、クエリ指向ツールに対するインジェクション攻撃への対策が実装され、ローカル開発環境とリモートホスティングの両方でより安全な運用が可能になった。さらに、規制環境向けのソブリンクラウドサポートとして、Azure US GovernmentおよびAzure operated by 21Vianetへの設定対応も追加された。これにより、コンプライアンス要件の厳しい政府機関や特定地域での採用が容易になる。
