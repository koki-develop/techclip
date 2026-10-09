---
date: "2026-10-10T08:12:09+09:00"
title: "Googleが汎用AIエージェント「Gemini agent」を発表、独自メールアドレスを持ち業務を代行"
description: "Googleは「Gemini at Work 2026」で業務全般を遂行する汎用AIエージェント「Gemini agent」を発表し、企業向けに展開を開始した。"
tags:
  - AI
  - Cloud
references:
  - "https://techcrunch.com/2026/10/08/google-brings-agentic-ai-to-gemini-starting-with-businesses/"
  - "https://blog.google/innovation-and-ai/infrastructure-and-cloud/google-cloud/gemini-at-work/"
---

## 概要

Googleは10月8日、「Gemini at Work 2026」カンファレンスで、Geminiを単なる対話型AIから実行型のエージェントへと進化させる新機能「Gemini agent」を発表した。単一のプロンプトウィンドウから知識作業、質問応答、コンテンツ作成、コーディングまでを横断的に処理できる汎用エージェントで、まず企業向けに展開を開始した。設計上の原則は「instructions（指示）ではなくobjectives（目標)」を与えるというもので、ユーザーが細かい手順を指示しなくても、エージェント自身が計画を立てて実行する点が特徴だ。

## 主な機能とアーキテクチャ

Gemini agentは、組織のビジネスコンテキスト全体にアクセスし、スキルやツールを活用しながら作業を計画・実行する。サブエージェントへ作業を委任できる仕組みを備え、複雑な業務タスクを単一の指示で計画・実行し、組織内のシステムと連携して成果物を仕上げることが可能だ。統合先はGoogle WorkspaceやMicrosoft 365、Slack、Jira、Confluence、BigQuery、Databricks、Snowflakeなど多岐にわたり、Model Context Protocol（MCP）サーバーにも対応する。

特に注目されるのは、エージェントが「職場アイデンティティ」を持つ点だ。Gemini agentは専用のメールアドレスと独自のコンテキストを保持し、チーム構成やタイムゾーン、承認権限を認識した上で、処理内容の監査証跡を生成する。これにより、人間の従業員に近い形で組織内のワークフローに組み込まれることになる。また、エージェントは職務に最適なモデルを自動選択する仕組みを持ちながら、ユーザーが用途に応じてAnthropicのClaudeなど第三者モデルを選べる柔軟性も備える。将来的にはオープンソースモデルやプライベートモデルへの対応も予定されている。コスト管理機能も組み込まれており、企業が利用料を制御しやすい設計になっている。

## 企業向けからの展開と競争環境

Googleは消費者向けに先駆けて企業向けからGemini agentの展開を始めた理由として、セキュリティ、スケール、パフォーマンスといった課題を先に解決する狙いがあるとしている。早期テスターにはOn、Shopify、PayPalが名を連ね、大企業顧客としてBNP Paribas、Merck、Ulta Beautyなどが挙げられている。

この発表の背景には、企業向けAIエージェント市場での競争激化がある。GoogleはGeminiの月間利用者数が10億人を超え、Fortune 100企業の約9割がGemini Enterpriseを採用していることを強調しており、OpenAIの「ChatGPT Dots」やMetaの「Muse」といった消費者向けエージェントの台頭を背景とした動きとみられる。業務アプリやシステムを横断して自律的にタスクを遂行するエージェントは各社が注力する領域であり、Googleは自社のクラウド基盤と既存の企業導入実績を武器に、この競争で存在感を強めたい考えだ。
