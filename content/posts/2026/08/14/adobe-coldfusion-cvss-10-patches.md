---
date: "2026-08-14T14:29:49+09:00"
title: "AdobeがColdFusionとCampaign Classicの緊急パッチを公開、CVSS満点10.0の脆弱性3件を含む計18件を修正"
description: "Adobeが8月11日、ColdFusionとCampaign ClassicにCVSS満点10.0を含む重大な脆弱性を修正するセキュリティアップデートを公開し、管理者に「Priority 1」として直ちにパッチを適用するよう呼びかけた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/08/adobe-patches-three-cvss-100-coldfusion.html"
  - "https://www.securityweek.com/adobe-urges-immediate-patching-of-critical-coldfusion-campaign-classic-flaws/"
  - "https://fieldeffect.com/blog/adobe-patches-coldfusion-campaign-classic"
---

## 概要

Adobeは2026年8月11日、ColdFusionとCampaign Classicを対象に緊急のセキュリティアップデートを公開した。両製品合わせて計18件の脆弱性が修正され、うちColdFusionで1件、Campaign Classicで2件、合計3件がCVSS満点となる10.0を記録している。Adobeはこれらを最も深刻度の高い「Priority 1」に分類し、管理者に対して直ちにパッチを適用するよう強く呼びかけている。現時点でこれらの脆弱性が実際に悪用された事例は確認されていないが、影響範囲の大きさと深刻度の高さから、各セキュリティメディアが一斉に注意喚起を行っている。

## ColdFusionの脆弱性

ColdFusionでは15件のセキュリティ欠陥が修正され、うち3件が最高水準の重大度「Critical」に分類される。最も深刻なのはOSコマンドインジェクションの脆弱性CVE-2026-48362(CVSS 10.0)で、悪用されればサーバーの完全なコンプロマイズ、データ露出、接続システムへの不正アクセスにつながる恐れがある。次いでevalインジェクションの脆弱性CVE-2026-48273(CVSS 9.9)があり、任意のコード実行やビジネスデータの露出を招く可能性がある。さらに認可制御の不備によるCVE-2026-71384(CVSS 9.6)は、サービス拒否(DoS)攻撃の引き金となり得る。影響を受けるのはColdFusion 2025.0.11以前および2023.0.22以前のバージョンで、それぞれ2025 Update 12(バージョン2025.0.12)と2023 Update 23(バージョン2023.0.23)で修正されている。

## Campaign Classicの脆弱性

Campaign Classicでは3件の重大な脆弱性が修正された。認可検証の不備に起因するCVE-2026-71398とCVE-2026-27302はいずれもCVSS 10.0の最大スコアを記録しており、前者は任意のコード実行、後者は不正アクセスによる顧客情報の露出につながる恐れがある。加えてSQLインジェクションの脆弱性CVE-2026-48381(CVSS 9.0)は、データの改ざんや露出を引き起こしうる。影響を受けるのはCampaign Classic v7バージョン7.4.3ビルド9399以前で、v7バージョン7.4.4ビルド9400で修正されている。なお、これらのパッチはオンプレミス展開のみを対象としており、Adobeがホストするクラウド版はすでに修復済みとされている。

## 悪用状況と今後の見通し

Adobeは現時点でこれらの脆弱性に対する既知の悪用は確認していないとしている。一方で、今回と同じ8月のパッチサイクルで修正されたAdobe Commerceの脆弱性CVE-2026-71362では、アドバイザリ公開後まもなく悪用が確認されたと報告されており、また数週間前に公開されたColdFusionの脆弱性CVE-2026-48282でも能動的な悪用が確認された前例がある。セキュリティ専門家は、技術詳細が公開されてから実際の攻撃(PoC開発や悪用)に至るまでの時間がAI支援による脆弱性分析の進展で短縮される傾向にあると指摘しており、今回のような重大脆弱性についても悪用までの猶予は限られるとみられる。Adobeが72時間以内という異例の短期間でのパッチ適用を推奨しているのはこうした背景を踏まえたものであり、ColdFusionおよびCampaign Classicをオンプレミスで運用する組織は速やかな対応が求められる。
