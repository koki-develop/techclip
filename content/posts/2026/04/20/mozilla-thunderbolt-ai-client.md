---
date: "2026-04-20T18:33:14+09:00"
title: "MozillaのMZLA、エンタープライズ向けオープンソースAIクライアント「Thunderbolt」を発表——CopilotやChatGPT Enterpriseに対抗"
description: "MozillaのMZLA Technologiesが、MPL 2.0ライセンスで公開するセルフホスト型エンタープライズAIクライアント「Thunderbolt」を発表し、データ主権と自社インフラ上でのAI活用を訴求した。"
tags:
  - OSS
  - AI
references:
  - "https://www.phoronix.com/news/Mozilla-Thunderbolt"
  - "https://www.theregister.com/2026/04/16/mozilla_thunderbolt_enterprise_ai_client/"
  - "https://www.ghacks.net/2026/04/20/mozillas-mzla-technologies-launches-thunderbolt-an-open-source-self-hosted-enterprise-ai-client/"
  - "https://www.omgubuntu.co.uk/2026/04/mozilla-thunderbolt-ai-client"
  - "https://www.helpnetsecurity.com/2026/04/17/mozilla-thunderbolt-open-source-ai-client-enterprise-data-control/"
---

## 概要

MozillaのMZLA Technologies（Thunderbirdメールクライアントで知られるMozilla Foundationの営利子会社）は2026年4月16日、エンタープライズ向けオープンソースAIクライアント「Thunderbolt」を発表した。MPL 2.0ライセンスのもとGitHubで公開されており、企業が自社インフラ上でセルフホストしながらAIを活用できるよう設計されている。Microsoft Copilot、ChatGPT Enterprise、Claude Enterpriseといった大手SaaS型AIサービスに対するオープンな代替として位置付けられており、ベンダーロックインとデータ管理への懸念に直接応えるものだ。

MZLA CEOのRyan Sipesは「私たちが今日解決しようとしている問題は、主権とコントロールの問題だ。AIはアウトソースするには重要すぎる」と述べ、組織がAIインフラを外部サービスに依存するのではなく、自らの手で管理すべきだという考えを強調した。

## 技術アーキテクチャと主な機能

Thunderboltは、チャット・検索・リサーチといった機能を統合した「AIワークスペース」として機能する。deepsetのHaystackプラットフォームと連携することでバックエンドシステムとエージェントワークフローを一元化できるほか、Model Context Protocol（MCP）サーバーおよびAgent Client Protocol（ACP）対応エージェントをサポートしている。これにより既存の社内データパイプラインを大規模に改修することなく接続できる。

対応プラットフォームはWindows・macOS・Linux・iOS・Androidと幅広く、Webクライアントも提供される。利用するAIモデルは組織が自由に選択でき、商用クラウドモデルのほか、オープンソースモデルや完全ローカルホスト型のモデルにも対応する。機密データを単一マシン上で処理することも可能だ。ワークフロー自動化機能として、スケジュール設定によるブリーフィング生成・トピック監視・レポート作成・イベント連動動作なども実装されている。セキュリティ面では、デバイスレベルのアクセス制御とオプションのエンドツーエンド暗号化が用意されている。現在、エンタープライズ向け本番利用に向けたセキュリティ監査が進行中だ。

## ビジネスモデルと提供形態

ソースコードはGitHubで誰でも利用可能だが、MZLAはエンタープライズ向けにサポート・カスタマイズ・デプロイメント支援を有償提供することで収益化を図る。また、小規模チーム向けにはクラウドホスト版（マネージドサービス）の提供も計画されている。早期アクセスの申し込みはthunderbolt.ioで受け付けており、統合パートナーによるストレージ・インフラ管理・エンジニアリングサポートも用意される予定だ。

## 背景と戦略的意義

MZLAはMozilla Foundationが設立した営利部門であり、オープンソースとビジネスの両立を掲げている。Sipesは過去のFirefox躍進になぞらえ、Thunderboltを大手AI企業の市場独占に対抗する「反乱同盟」の一環として位置付けた。エンタープライズAI市場ではMicrosoft・OpenAI・Anthropicなど大手プロバイダーへの依存が進む一方、データ主権・プライバシー・コスト透明性への関心も高まっており、Thunderboltはそうした需要に応える選択肢として注目される。オープンソースコミュニティによる拡張や監査が可能な点も、エンタープライズ採用の後押しになると期待される。
