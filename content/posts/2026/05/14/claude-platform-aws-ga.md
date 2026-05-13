---
date: "2026-05-14T02:46:39+09:00"
title: "AnthropicのClaudeプラットフォームがAWSで一般公開、既存アカウントから直接利用可能に"
description: "AWSが2026年5月11日、Claude Platform on AWSの一般提供開始を発表し、既存のAWSアカウントからAnthropicのネイティブプラットフォームに直接アクセスできるようになった。"
tags:
  - AI
  - Cloud
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/05/claude-platform-aws/"
  - "https://thenewstack.io/anthropics-claude-platform-comes-to-aws/"
---

## 概要

Amazonは2026年5月11日、Claude Platform on AWSの一般提供（GA）開始を発表した。これにより、企業は既存のAWSアカウントを通じてAnthropicのネイティブClaude Platformに直接アクセスできるようになった。AWSは「クラウドプロバイダーとして初めてネイティブClaude Platformエクスペリエンスへのアクセスを提供する」とアピールしており、別途Anthropicアカウントを作成・管理する手間なく、統合されたクラウド環境からClaudeの機能を活用できる点が特長だ。

これまでAnthropicのClaudeをAWS環境で利用するにはAmazon Bedrockを介したAPIアクセスが主な手段であったが、今回のGA化によりAnthropicネイティブの体験がAWSアカウントから直接提供されるようになった。企業にとってはアカウント管理の一元化や請求の統合が実現し、AI導入の障壁が大幅に低下する。

## 利用可能な機能

今回のリリースで利用できる主な機能は以下の通りだ。Claude Managed Agents（ベータ）とアドバイザー戦略（ベータ）によりエージェント型AIワークフローの構築が可能になるほか、Web検索・Web取得、コード実行、Files API（ベータ）、スキル（ベータ）、MCPコネクタ（ベータ）といった実用的なツール群が揃っている。また、プロンプトキャッシング、引用機能、バッチ処理、Claude Consoleも利用可能で、開発から運用まで一貫したプラットフォームを提供する。

## セキュリティと運用体制

セキュリティ面では、Claude Platform on AWSはAnthropicが運営・管理するサービスであり、顧客データはAWSのセキュリティ境界外で処理される点に注意が必要だ。一方で、既存のIAM認証情報をそのまま活用できるほか、AWS統合請求によるコスト管理、CloudTrail監査ログによる操作履歴の追跡が可能となっており、エンタープライズ環境での運用管理を支援する。

## 提供リージョンと展望

サービスは北米・南米・欧州・アジア太平洋地域を含む全17リージョンで提供される。グローバルな展開体制によりデータレジデンシーの要件にも対応しやすくなっており、多国籍企業や規制の厳しい業界での採用が期待される。AnthropicとAWSの連携強化は、MicrosoftとOpenAIの関係に対抗する形でのクラウドAI市場の競争激化を示しており、今後の機能拡充にも注目が集まる。
