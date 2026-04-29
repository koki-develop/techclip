---
date: "2026-04-30T02:37:03+09:00"
title: "OpenAIがMicrosoft独占を終了しAmazon Bedrockへ展開、GPT最新モデル・Codex・Managed Agentsが利用可能に"
description: "OpenAIがMicrosoftとのクラウド独占提供契約を改定し、最新フロンティアモデルやCodex、Managed AgentsをAmazon Bedrockで限定プレビュー提供開始した。"
tags:
  - AI
  - Cloud
references:
  - "https://techcrunch.com/2026/04/28/amazon-is-already-offering-new-openai-products-on-aws/"
  - "https://www.cnbc.com/2026/04/28/openai-brings-models-to-aws-after-ending-exclusivity-with-microsoft.html"
  - "https://aws.amazon.com/about-aws/whats-new/2026/04/bedrock-openai-models-codex-managed-agents/"
---

## 概要

2026年4月28日、AWSとOpenAIは提携拡大を発表し、Amazon BedrockでOpenAIの最新フロンティアモデル、コーディングエージェントのCodex、そして新サービスのManaged Agentsが限定プレビューとして提供開始された。これはOpenAIがMicrosoftと締結していたクラウド独占提供契約を改定し、Microsoft Azure AI以外のプラットフォームでもOpenAIモデルが利用できるようになった歴史的な転換点だ。AmazonのAndy Jassy CEOはこの発表を受け「非常に興味深い発表」とSNSで反応を示した。

## 提供される3つのサービス

Amazon Bedrockで新たに利用可能になったOpenAIのサービスは以下の3つ。

**最新フロンティアモデル**：AWS顧客がBedrockを経由して初めてOpenAIのフロンティアモデルにアクセス可能になった。IAM、AWS PrivateLink、ガードレール、暗号化、CloudTrailロギングといったAWSのエンタープライズセキュリティコントロールをそのまま継承できる点が特徴で、既存のAWSクラウドコミットメントに利用量を適用できる。

**Codex**：OpenAIのコーディングエージェントをAWS環境に統合したもので、Codex CLI、デスクトップアプリ、VS Code拡張機能から利用可能。AWS認証情報で認証し、Bedrock経由で推論を実行する。

**Managed Agents**：OpenAIのフロンティアモデルとエージェントハーネスを組み合わせた新サービスで、本番環境対応のAI駆動型エージェントを迅速にデプロイできる。各エージェントは独自のIDを持ち、全アクションがログに記録されるため、監査やコンプライアンス対応も容易だ。

## 独占終了の背景とクラウドAI競争の新局面

OpenAIがMicrosoftとの独占提供契約を改定した背景には、2026年2月に発表されたAmazonによる最大500億ドル規模の出資が絡んでいる。Amazonの大型投資はMicrosoftの独占権と法的に衝突しており、今回の独占解消はその問題を解決する形で実現した。これによりOpenAIはAWSおよびOracleとも協力関係を深めており、マルチクラウド戦略への転換が鮮明になった。

一方、MicrosoftはOpenAIとの関係が緊張しつつあるとの報道を受け、Anthropicと連携して新たなエージェント機能の開発を進めている。エンタープライズ向けAIプラットフォームの主導権争いは、OpenAI対Anthropicという構図から、AWS・Azure・Google Cloudがそれぞれ異なるAIパートナーを抱える複雑な多極構造へと移行しつつある。Bedrockを通じてOpenAIモデルをAWSのセキュリティ基盤と組み合わせて利用できるようになったことで、クラウドネイティブなエンタープライズユーザーにとっての選択肢は大幅に広がった。
