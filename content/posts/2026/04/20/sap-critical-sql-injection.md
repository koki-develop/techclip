---
date: "2026-04-20T18:33:14+09:00"
title: "SAPが4月パッチでCVSS 9.9の重大SQLインジェクション脆弱性CVE-2026-27681を修正"
description: "SAPの2026年4月パッチデーで、SAP BPCおよびBWに存在するCVSS 9.9の重大なSQLインジェクション脆弱性CVE-2026-27681を含む計19件の脆弱性が修正された。"
tags:
  - Security
references:
  - "https://www.heise.de/en/news/SAP-Patchday-One-critical-SQL-injection-vulnerability-and-18-others-11256718.html"
---

## 概要

SAPは2026年4月のパッチデーにおいて、CVSS スコア9.9の重大な脆弱性CVE-2026-27681を含む計19件のセキュリティノートを公開した。CVE-2026-27681はSAP Business Planning and Consolidation（BPC）およびSAP Business Warehouse（BW）に存在するSQLインジェクションの欠陥で、認証済みの低権限ユーザーが細工したSQL文を実行することで、データベース上のデータを読み取り・変更・削除できる可能性がある。財務データの窃取やシステム全体の侵害につながる深刻なリスクがあり、ITマネージャーには直ちにパッチを適用するよう呼びかけられている。

## 主要脆弱性の詳細

最も深刻なCVE-2026-27681は、「不十分な認可チェック」に起因するSQLインジェクション脆弱性だ。CVSS 9.9という最高水準に近いスコアが示す通り、悪用されれば業務中核の財務・計画データが攻撃者の手に渡りかねない。対象製品であるSAP BPCとSAP BWは多くの大企業で予算管理や経営分析に利用されており、侵害の影響範囲は広い。

2番目に深刻な脆弱性CVE-2026-34256（CVSS 7.1）は、SAP ERPおよびSAP S/4HANA（プライベートクラウド・オンプレミス）に影響する認可チェック不備の問題だ。認証済み攻撃者が特定のABAPレポートを実行し、既存の8桁実行可能ABAPレポートを不正に上書きできるため、業務アプリケーションの意図した機能が失われるリスクがある。

## その他の修正と推奨対応

今回のパッチデーでは上記2件のほかに、SAP BusinessObjects、Human Capital Management、S/4HANAの各バリアント、NetWeaver Application Server、HANA Cockpitに影響する中程度のリスクを持つ15件の脆弱性と、NetWeaver Application Server ABAPおよびLandscape Transformationに関する低リスク2件も合わせて修正されている。SAPは脆弱なソフトウェアを使用しているかどうかを確認し、特にCVSS 9.9の重大SQLインジェクション脆弱性については最優先でパッチを適用するよう強く推奨している。
