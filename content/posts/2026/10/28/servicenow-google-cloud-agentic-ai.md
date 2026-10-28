---
date: "2026-10-28T18:11:04+09:00"
title: "ServiceNowとGoogle Cloud、Action FabricとGemini Enterpriseを連携——業務ワークフローにエージェントAIを統合"
description: "ServiceNowとGoogle Cloudが提携を拡大し、Action FabricとGemini EnterpriseをMCPとA2Aで接続、小売・CRM・IT運用などの業務ワークフローをAIエージェントから直接実行できるようにした。"
tags:
  - Cloud
  - AI
references:
  - "https://www.googlecloudpresscorner.com/2026-10-27-ServiceNow-and-Google-Cloud-advance-agentic-AI-for-industry-workflows"
---

## 概要

ServiceNowとGoogle Cloudは10月27日、両社の提携を拡大し、ServiceNowのワークフロー実行基盤「Action Fabric」とGoogle Cloudの「Gemini Enterprise」を接続すると発表した。これにより、Gemini Enterprise上で動くAIエージェントが、ServiceNowが管理する小売店舗運用、フィールドサービス管理、通信事業者向けサービス管理、CRM、ITサービス管理(ITSM)、IT運用管理(ITOM)、構成管理データベース(CMDB)といった業務ワークフローを、複数ステップにわたる複雑なアクションとして直接実行できるようになる。利用者が普段使っているAIアシスタントを離れずに、基幹業務のタスクを完了できる点が狙いだ。

## 技術的な統合の仕組み

両社はこの統合に、Model Context Protocol(MCP)サーバーとAgent2Agent(A2A)接続を採用した。これにより、ServiceNow側のワークフローをヘッドレスな形でGemini Enterpriseに組み込み、エージェントがServiceNowのガバナンスや権限管理を維持したまま業務システムを操作できるようにしている。対応コネクタはGoogle Cloud Marketplaceで公開され、デモやリファレンスアーキテクチャも併せて提供される予定で、企業が自社環境に導入しやすい形が意識されている。

## 当初の活用事例と提供時期

発表時点で4つの統合シナリオが示されている。小売業界向けの「設備診断とサービス技術者のディスパッチ」、CRM領域の「商談管理と見積書生成」、IT運用領域の「インシデントトリアージとセルフサービス解決」の3つは既に一般提供が開始されている。一方、通信事業者向けの「アカウント管理とケーストリアージ」は2027年初頭の提供を予定しており、業界別の展開には時間差が設けられている。

## 戦略的な狙いと今後の展望

ServiceNowのJohn Aisien SVPは「ワークフローのオーケストレーションとガバナンスをGemini Enterpriseと組み合わせることで、チームは使い慣れたAIアシスタントを離れずにミッションクリティカルなタスクを実行できる」と述べた。Google CloudのSatish Thomas VPも「この協業はミッションクリティカルなServiceNowシステムにエージェントの力をもたらし、複雑な課題をより速く解決できるようにする」とコメントしている。両社は、セキュリティや低レイテンシ、ガバナンス水準を維持しながらエージェントAIの活用を企業全体に広げることを狙いとしており、今後も対応業務領域を段階的に拡大していく方針とみられる。
