---
date: "2026-08-06T02:29:24+09:00"
title: "Anaconda、AIセキュリティ企業Enkrypt AIを買収 MCPサーバーの脆弱性13万件超を検出した実績を統合へ"
description: "データサイエンス基盤大手のAnacondaがAIセキュリティ企業Enkrypt AIを買収し、AI開発から本番運用までのライフサイクル全体にセキュリティ機能を統合する。"
tags:
  - AI
  - Security
references:
  - "https://www.anaconda.com/blog/anaconda-acquires-enkrypt-ai"
  - "https://www.hpcwire.com/aiwire/2026/08/04/anaconda-acquires-enkrypt-ai-to-secure-the-trillion-token-enterprise/"
  - "https://www.shashi.co/2026/08/anaconda-buys-enkrypt-ai-after-finding.html"
---

## 概要

データサイエンス・機械学習プラットフォームを展開するAnacondaは8月4日、AIセキュリティ企業Enkrypt AIを買収すると発表した。この買収により、企業がAIモデルやAIエージェントを開発してから本番環境で運用するまでのライフサイクル全体に、セキュリティおよびガバナンス機能を統合する狙いだ。買収の背景には、企業のAI活用が急拡大する一方で、AIエージェントが実際に何を行っているかを組織側が十分に把握できていないという課題がある。

## Enkrypt AIの実績

Enkrypt AIは、Anthropic、Mistral、OpenAI、Google Gemini、DeepSeekなど主要AIプロバイダーの各種モデルを対象に、300種類以上の攻撃カテゴリーに基づくレッドチーミング(疑似攻撃による脆弱性診断)を実施してきた実績を持つ。同社が実施したスキャン調査では、25,000のMCP(Model Context Protocol)サーバー上に存在する268,000件のツールを分析した結果、143,000件以上の脆弱性が発見され、対象サーバーの73%が何らかの影響を受けていたという。MCPサーバーはAIエージェントが外部ツールやデータソースと連携するための標準インターフェースとして急速に普及しており、その安全性を巡る懸念が高まっていた中での調査結果となる。

## 統合される機能とAnaconda Platformの構成

買収後、Enkrypt AIの技術はAnaconda Platformの新たな「セキュリティ層」として組み込まれる。Anaconda Platformは、オープンソースパッケージやモデル管理を担う基盤層、AI-native開発ワークフローを支えるオーケストレーション層、Kilo Codeによるエージェント開発環境であるエンジニアリング層、そして今回追加されるセキュリティ・ガバナンス層という多層構造になる。具体的には、本番投入前のセキュリティテスト、実行時(ランタイム)の防御機能、NIST AI Risk Management FrameworkやEU AI Actへの準拠を自動化する仕組み、監査証跡の生成などが提供される。これにより、特にオープンウェイトモデルを利用する企業が、自社のセキュリティ・コンプライアンス要件を実行可能な制御ルールへと変換し、独自のガードレールを定義・適用できるようになる。

## 今後の展望

Anaconda CEOのDavid DeSanto氏とEnkrypt AI共同創業者兼CEOのSahil Agarwal氏は共同で、「開発の速度とセキュリティは互いに排斥し合うものではない」とのメッセージを打ち出している。月間1兆トークン規模でAIが利用される「トリリオン・トークン・エンタープライズ」の時代において、AIエージェントの安全性を担保しながら開発速度を落とさない仕組みづくりが今後の焦点となりそうだ。
