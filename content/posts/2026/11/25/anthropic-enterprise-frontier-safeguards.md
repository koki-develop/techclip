---
date: "2026-11-25T18:09:55+09:00"
title: "Anthropic、複数リクエストをまたいだ不正利用を検知する「Enterprise Frontier Safeguards」公開ベータを提供開始"
description: "Anthropicはゼロデータリテンションを保ちながら企業の不正利用を検知する「Enterprise Frontier Safeguards」の公開ベータを開始し、AWSやGoogle Cloudなどに対応した。"
tags:
  - AI
  - Security
references:
  - "https://claude.com/resources/articles/zero-data-retention-with-enterprise-frontier-safeguards"
  - "https://www.securityweek.com/anthropic-expands-enterprise-safeguards-for-detecting-ai-misuse/"
---

## 概要

Anthropicは11月23日、企業向けClaudeの不正利用を自動検知する新機能「Enterprise Frontier Safeguards(EFS)」の公開ベータを開始した。従来のClaudeの保護機能は個々のリクエストを単体で分析するものに限られていたが、EFSはこれに加えて、複数のリクエストをまたいで疑わしい利用パターンを検知する監視層を新たに導入する。これにより、攻撃を複数のエージェントやリクエストに分散させることで個別には無害に見えるよう仕組まれた不正利用も、集約的な分析によって浮き彫りにできるという。対象はゼロデータリテンション(ZDR)契約のもとでClaudeを利用する企業で、Anthropicによれば100社以上の顧客からの意見を取り入れ、StripeやSalesforceを含むフォーチュン100企業の4分の1が開発に協力した。

## ゼロデータリテンションとの両立

EFSの特徴は、不正利用検知とゼロデータリテンションという本来相反しがちな要件を両立させている点にある。企業の会話データは自社管理のクラウドストレージに保存され、独自の暗号化キーとアクセスポリシーで保護される。Anthropicおよびクラウドプロバイダーは、転送後にそのデータのコピーを保持しない。自動安全監視の仕組みは顧客環境内でパターン分析を行い、「Safety Cases」と呼ばれる検知結果を生成するが、Anthropicが受け取るのは監視メタデータのみであり、会話内容そのものは渡されない。生成されたSafety Caseは顧客側で検証・管理する運用になっている。

## 対応プラットフォームと導入企業

現時点でEFSが対応しているのはClaude Platform、Claude Platform on AWS、Amazon Bedrock、Google Cloudで、Microsoft Foundryへの対応も近く提供される予定だ。すでにComcast、Stripe、Cisco、Wells Fargo、KPMGといった大手企業が評価を進めており、医療・金融・法務など、データの機密性が特に重視される規制業界でのAI活用を後押しする狙いがある。

## 背景と今後の展望

Anthropicは同時期に、エンタープライズ向けコーディングエージェントのセキュリティに関するガイドも公開しており、プロンプトインジェクション検知メカニズムの導入によって攻撃成功率を90%から28%まで低減できたと説明している。EFSとこれらの取り組みは、企業がデータ主権やプライバシー要件を維持したまま、より高度なAIエージェントの活用を進められるようにするという、Anthropicの一連のエンタープライズ向けセキュリティ投資の一環と位置付けられる。
