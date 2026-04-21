---
date: "2026-04-22T02:29:12+09:00"
title: "CISAがCisco SD-WAN等8件の脆弱性をKEVに追加、連邦機関に早期パッチ適用を義務化"
description: "CISAがCisco Catalyst SD-WAN ManagerやPaperCut NG/MFなど8件の悪用済み脆弱性をKEVカタログに追加し、連邦機関に対して4月23日または5月4日までのパッチ適用を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/cisa-adds-8-exploited-flaws-to-kev-sets.html"
  - "https://www.cisa.gov/news-events/alerts/2026/04/20/cisa-adds-eight-known-exploited-vulnerabilities-catalog"
  - "https://www.helpnetsecurity.com/2026/04/21/cisa-flags-another-cisco-catalyst-sd-wan-manager-bug-as-exploited-cve-2026-20133/"
---

## 概要

米国サイバーセキュリティ・インフラセキュリティ庁（CISA）は2026年4月20日、Cisco Catalyst SD-WAN Manager、PaperCut NG/MF、JetBrains TeamCityなど複数の製品に関する8件の脆弱性を「既知の悪用脆弱性（KEV）カタログ」に追加した。これらはいずれも実際の攻撃での悪用が確認されており、米国連邦民間行政機関（FCEB機関）に対してはCisco関連の3件について2026年4月23日まで、残る5件については2026年5月4日までのパッチ適用が義務付けられた。

## 追加された8件の脆弱性

今回KEVカタログに追加された脆弱性の内訳は以下の通り。

- **CVE-2026-20122**（CVSS 5.4）— Cisco Catalyst SD-WAN Manager。ファイルアップロード機能を悪用してvmanageユーザー権限を取得される可能性がある。
- **CVE-2026-20128**（CVSS 7.5）— Cisco Catalyst SD-WAN Manager。認証済みのローカル攻撃者がDCAユーザー権限を取得できる。
- **CVE-2026-20133**（CVSS 6.5）— Cisco Catalyst SD-WAN Manager。リモートの攻撃者が機密情報を閲覧できる情報漏洩の脆弱性。Ciscoはまだ公式に悪用を認めていないが、セキュリティ研究者は「防御者が認識する以上に高リスク」と評価している。
- **CVE-2023-27351**（CVSS 8.2）— PaperCut NG/MF。`SecurityRequestFilter`クラス経由で認証を回避できる。Lace TempestによるCl0pおよびLockBitランサムウェアの配布に利用されたことが確認されている。
- **CVE-2024-27199**（CVSS 7.3）— JetBrains TeamCity。相対パストラバーサルにより限定的な管理者アクションを実行可能。
- **CVE-2025-2749**（CVSS 7.2）— Kentico Xperience CMS。認証済みユーザーのStaging Sync Serverを通じて任意のデータを相対パスへアップロードできる。
- **CVE-2025-32975**（CVSS 10.0）— Quest KACE Systems Management Appliance。認証回避により正規認証なしでユーザーへのなりすましが可能。Arctic Wolfが2026年3月に未パッチシステムへの実際の悪用を検出している。
- **CVE-2025-48700**（CVSS 6.1）— Synacor Zimbra Collaboration Suite。クロスサイトスクリプティング（XSS）により機密情報へのアクセスが可能。

## 注目点と背景

今回追加された8件のうち、Cisco Catalyst SD-WAN Managerに関する3件（CVE-2026-20122、CVE-2026-20128、CVE-2026-20133）は対応期限が2026年4月23日と非常に短く設定されており、CISAが即時対応を強く求めていることが伺える。CVE-2026-20122とCVE-2026-20128については2026年3月の時点で積極的な悪用が確認されており、CISAの緊急度の高さを裏付けている。

また、CVE-2025-32975はCVSSスコア10.0と最高評価の深刻度を持つ脆弱性で、Quest KACEの認証機構を完全に回避できる。PaperCutの脆弱性（CVE-2023-27351）はLace Tempestによるランサムウェア攻撃への利用実績があり、組織のファイル管理インフラへの直接的な脅威となっている。KEVカタログへの登録はBOD 22-01指令に基づく法的拘束力のある指示であり、該当製品を使用する組織は対応期限内にパッチ適用または利用停止の措置を講じる必要がある。
