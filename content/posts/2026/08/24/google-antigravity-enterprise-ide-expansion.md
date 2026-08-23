---
date: "2026-08-24T02:04:01+09:00"
title: "Google、AIコーディングエージェント「Antigravity」をJetBrains・Zedにも展開、Gemini Enterpriseで企業統制機能を強化"
description: "GoogleがAIコーディングエージェント「Antigravity」をJetBrainsやZedなど主要IDEへ拡大し、Gemini Enterpriseサブスクリプションに統合して予算管理やアクセス制御などの企業向け機能を追加した。"
tags:
  - AI
  - Programming Languages
references:
  - "https://www.theregister.com/ai-and-ml/2026/08/21/google-tethers-antigravity-to-enterprise-controls-amid-ai-shakeup/5290730"
  - "https://itbrief.co.nz/story/google-adds-antigravity-to-gemini-enterprise-subscriptions"
---

## 概要

Googleは、DeepMind発のAIコーディングエージェント「Antigravity」の対応範囲を拡大し、これまで対応していたVisual Studio Codeに加えて、Visual Studio、JetBrains系IDE、Zedへの拡張機能提供をプレビューとして開始した。あわせてAntigravityをGemini Enterpriseのサブスクリプション（Standard、Plus、Standard Emerging Marketの各プラン）に統合し、企業の管理者が組織全体でAIコーディングエージェントの利用を一元管理できるようにした。Antigravityはデスクトップアプリ（v2.0）、CLI、SDK、IDE拡張という複数のインターフェースを通じて利用できるエージェント型の開発ツールであり、今回の展開により主要な開発環境のほぼすべてをカバーする形になった。

## エンタープライズ向け管理機能

新たに追加された管理機能は、大きく予算管理とセキュリティ・監査の2系統に分かれる。予算管理面では、プロジェクト単位での月間予算上限の設定、複数チーム間でのトークンプール共有、利用量が上限を超えた際の課金オプションなど、コストの可視化と統制を目的とした機能が用意された。セキュリティ・監査面では、ワークスペースやブラウザ、MCPサーバーへのアクセス制御、ターミナルでのコマンド実行に対するサンドボックス化や承認制の適用、プロンプトおよびレスポンスの監査ログ取得、Workforce Identity Federationへの対応などが盛り込まれている。これらはGoogle Cloudのデータ処理補足契約(DPA)に準拠する形で提供され、企業のデータプライバシー要件にも対応する。

## 背景

Googleによれば、これらの企業向け統制機能はエンタープライズ顧客からの要望を受けて実装されたものであり、AIコーディングエージェントを組織内で安全かつ管理可能な形で展開したいというニーズに応える狙いがある。導入企業の一つであるAccentureは、「セキュアで信頼できるGoogle Cloudの基盤のもと、最高レベルのテクノロジーで技術者を支援できる」とコメントし、今回の統合を評価している。一方でThe Registerは、この発表がDeepMindの組織再編や主要AI研究者の相次ぐ離脱など、Google社内のAI部門をめぐる一連の動揺("AIシェイクアップ")のさなかに行われた点を指摘しており、Antigravityのエンタープライズ強化はGoogleが競合の激しいAIコーディングツール市場での地位を固めようとする動きの一環とみられる。

## 今後の展望

JetBrainsおよびZed向けの拡張機能は現時点でプレビュー版としての提供にとどまっており、正式版への移行時期は明らかにされていない。今後、対応IDEの拡大や管理機能の追加が進めば、Antigravityは個人開発者向けツールから企業のソフトウェア開発基盤の一部としての位置づけをさらに強めていく可能性がある。
