---
date: "2026-04-15T02:32:48+09:00"
title: "CISAがKEVカタログに7件の脆弱性を追加——Fortinet・Microsoft・Adobe製品に実際の悪用を確認"
description: "米CISAはFortinet FortiClient EMS、Microsoft Exchange Server・Windows・VBA、Adobe Acrobatなどを対象とした7件の脆弱性を既知悪用脆弱性（KEV）カタログに追加し、連邦政府機関に最短4月16日までの修正を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/cisa-adds-6-known-exploited-flaws-in.html"
  - "https://securityaffairs.com/190775/security/u-s-cisa-adds-adobe-fortinet-microsoft-windows-microsoft-exchange-server-flaws-to-its-known-exploited-vulnerabilities-catalog.html"
---

## 概要

米国サイバーセキュリティ・インフラセキュリティ庁（CISA）は2026年4月14日、Fortinet・Microsoft・Adobe製品に存在する合計7件の脆弱性を「既知悪用脆弱性（KEV）カタログ」に追加した。いずれもCISAが悪用の証拠を確認したうえでKEVカタログに追加されたもので、BOD 22-01指令に基づき連邦政府機関には迅速なパッチ適用が義務付けられている。ただし、一部の脆弱性については公開された悪用報告がまだ確認されていない。最も緊急性が高いFortinet製品の脆弱性については修正期限が**4月16日**と極めて短く設定されており、民間組織に対しても早急な対応が強く推奨されている。

## 追加された脆弱性の詳細

今回追加された7件の脆弱性は以下のとおりである。

| CVE番号 | 製品 | 脆弱性の種類 | CVSSスコア | 修正期限 |
|---|---|---|---|---|
| CVE-2026-21643 | Fortinet FortiClient EMS | SQLインジェクション | 9.1 | 4月16日 |
| CVE-2023-21529 | Microsoft Exchange Server | 信頼できないデータの逆シリアル化 | 8.8 | 4月27日 |
| CVE-2026-34621 | Adobe Acrobat/Reader | プロトタイプポリューション | 8.6 | 4月27日 |
| CVE-2023-36424 | Microsoft Windows (Common Log File System Driver) | 境界外読み取り | 7.8 | 4月27日 |
| CVE-2025-60710 | Microsoft Windows Host Process | 不適切なシンボリックリンク処理 | 7.8 | 4月27日 |
| CVE-2020-9715 | Adobe Acrobat Reader | 解放後使用（Use-After-Free） | 7.8 | 4月27日 |
| CVE-2012-1854 | Microsoft Office VBA | 安全でないライブラリ読み込み（DLLハイジャック） | 7.8 | 4月27日 |

なかでも**CVE-2026-21643**（Fortinet FortiClient EMS）はCVSSスコア9.1と最も深刻度が高く、認証不要のリモート攻撃者がHTTPリクエストを細工するだけでSQLインジェクションを通じて任意コードを実行できる。悪用は2026年3月24日以降に確認されており、他の脆弱性より11日も早い修正期限が設けられた。

## 注目される脅威：Medusaランサムウェアとの関連

**CVE-2023-21529**（Microsoft Exchange Server）は、認証済み攻撃者が信頼できないデータを逆シリアル化することでリモートコード実行を可能にする脆弱性である。この脆弱性はすでに脅威アクター**Storm-1175**によって武器化されており、**Medusaランサムウェア**の配信に活用されていることが確認されている。Exchange Serverはインターネットに直接公開されているケースも多く、悪用の広がりが懸念される。

また、CVE-2012-1854（Microsoft VBA）のように10年以上前の古い脆弱性が今も実環境で悪用されていることは、依然として多くの組織で古いシステムやソフトウェアが使い続けられている現状を示している。

## 対応と推奨事項

CISAはBOD 22-01（拘束的運用指令22-01）に基づき、連邦政府機関に対して今回追加された脆弱性のパッチ適用を期限内に完了するよう義務付けている。民間企業や組織に対する法的な強制力はないものの、CISAは同様の対応を強く推奨している。

特にFortinet FortiClient EMSを使用している組織は、**4月16日**という極めて短い期限を考慮し、直ちにベンダーが提供するパッチまたはアップデートを適用することが求められる。Microsoft Exchange Serverについてはランサムウェア配布への悪用が確認されているため、インターネット公開環境での運用リスクを改めて評価することが重要だ。
