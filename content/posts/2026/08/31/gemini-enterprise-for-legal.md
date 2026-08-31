---
date: "2026-08-31T18:18:29+09:00"
title: "Google Cloud、法律事務所向けAIエージェント基盤「Gemini Enterprise for Legal」をプレビュー公開"
description: "Google Cloudが契約レビューや規制監視など法務業務に特化したエージェント型AI「Gemini Enterprise for Legal」を発表し、Cleary GottliebやFreshfieldsなど大手法律事務所が早期導入パートナーとして参加した。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise-for-legal"
  - "https://www.law.com/international-edition/2026/08/25/freshfields-cleary-and-weil-become-early-adopters-of-google-clouds-gemini-enterprise-for-legal/"
  - "https://legaltechnology.com/google-cloud-unveils-gemini-enterprise-for-legal/"
---

## 概要

Google Cloudは8月25日、法律実務に特化したエージェント型AIプラットフォーム「Gemini Enterprise for Legal」をプレビュー公開した。契約レビューや修正(redlining)、プレイブック作成、規制動向のスキャン、法律調査、データ主体アクセス要求(DSAR)対応といった法務業務を自動化することを狙った製品で、Cleary Gottlieb、Freshfields、Weil、Williams & Connollyといった大手法律事務所が早期導入パートナーとして参加していることも合わせて発表された。同日にはFinancial Services業界向けのGemini Enterpriseも同時にリリースされており、Google Cloudが業界特化型AIソリューションの展開を加速させていることがうかがえる。

## 4つのコアコンポーネント

Gemini Enterprise for Legalは大きく4つの要素で構成される。1つ目は法務向けに調整されたスキル群で、契約書のレビューや修正、プレイブックの自動生成、規制監視、法律調査、DSAR対応などを担い、企業固有の専門知識を実行可能な形で組み込める。2つ目は信頼できるシステムやデータへのセキュアな接続で、MCPコネクタを通じてiManageやNetDocumentsといった文書管理システム、DocuSignの契約管理、Everlaw・RelativityOneの電子証拠開示(eDiscovery)ツール、Thomson Reuters HighQやCourtListenerといった法律調査サービス、さらにHarveyやLegoraなど法務特化AIとも連携する。3つ目はGoogleが事前構築した規制スクリーニングや契約起草などのエージェントで、中央集権的なガバナンスの下で管理される。4つ目はAccenture、Deloitte、KPMGといったシステムインテグレーターや法務テック企業が加わるオープンなパートナーエコシステムだ。

## セキュリティとガバナンス、業界での位置づけ

法務業務は機密性や倫理的な情報隔壁(エシカルウォール)、権限管理への要求が特に厳しい領域であり、Gemini Enterprise for LegalはVPCやCMEKによる暗号化、既存のロールベースアクセス制御(RBAC)や文書レベルの権限設定の継承、監査ログの自動記録といった機能を備える。Google Cloudは、顧客のデータやプレイブック、知的財産は組織内でのみプライベートに扱われ、基盤モデルの学習や微調整には利用しないと説明している。また出力にはすべて検証可能な根拠(グラウンディング)と追跡可能な引用が付与され、法律業務で不可欠な正確性の担保を図っている。legaltechnology.comは、汎用AIツールとは異なり法務業界固有の要件に特化して設計されている点を、一般的な生成AI製品との差別化ポイントとして挙げている。

## 今後の展望

Google Cloudは今回のLegal・Financial Services向けに続き、Healthcare、Life Sciences、その他Professional Services分野への業界特化型Gemini Enterprise展開も予定していると述べている。価格体系はプレビュー段階では明らかにされていないが、Cleary GottliebやFreshfields、Weilといった国際的な大手法律事務所が早期から採用を表明していることは、エージェント型AIが法務の定型業務だけでなく訴訟支援など高度な業務領域にも浸透しつつあることを示している。今後はiManageやRelativityOneなど既存の法務インフラとの統合の深さや、実際の業務現場での精度・信頼性が、他の法務特化AI(HarveyやLegoraなど)との競争を左右する焦点になりそうだ。
