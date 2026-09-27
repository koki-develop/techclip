---
date: "2026-09-28T08:11:20+09:00"
title: "CISAがWSO2・Adobe Commerce・SharePoint・Mikrotik RouterOSの悪用中脆弱性4件をKEVに追加、連邦機関に緊急対応命令"
description: "CISAはWSO2、Adobe Commerce、Microsoft SharePoint、Mikrotik RouterOSの実際に悪用されている脆弱性計4件をKnown Exploited Vulnerabilitiesカタログに追加し、連邦機関に9月27〜28日までの対応を義務付けた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/cisa-warns-of-sharepoint-wso2-adobe-commerce-flaws-exploited-in-attacks/"
  - "https://thehackernews.com/2026/09/wso2-and-adobe-commerce-flaws-exploited.html"
  - "https://securityaffairs.com/199777/hacking/u-s-cisa-adds-microsoft-sharepoint-and-mikrotik-routeros-flaws-to-its-known-exploited-vulnerabilities-catalog.html"
---

## 概要

米サイバーセキュリティ・インフラセキュリティ庁(CISA)は、実際の攻撃で悪用が確認された脆弱性4件をKnown Exploited Vulnerabilities(KEV)カタログに追加したと発表した。WSO2製品群(CVE-2026-5430)とAdobe Commerce/Magento(CVE-2026-71362)は9月24日に、Microsoft SharePoint Server(CVE-2026-65660)とMikrotik RouterOS(CVE-2026-67279)は9月25日に、それぞれ追加された。連邦機関に対しては拘束的運用指令(BOD)22-01に基づき、WSO2とAdobe Commerceの2件は9月27日、SharePointとRouterOSの2件は9月28日までの対応が義務付けられている。

## WSO2とAdobe Commerce、深刻度9点台の重大脆弱性

CVE-2026-5430はWSO2 API Control Plane、API Manager(バージョン4.1.0〜4.6.0)、Traffic Manager、Universal Gateway(バージョン4.5.0・4.6.0)に存在するパストラバーサルの脆弱性で、CVSSスコアは最大値に近い9.8。任意ファイルのアップロードを許し、リモートコード実行(RCE)にまで発展しうる。セキュリティ企業watchTowrは、公開された技術詳細がないにもかかわらず、9月13日の時点でハニーポットに対し偽造JWTトークンを用いた攻撃試行を観測したと報告している。原因はJWT認証機構が非対応アルゴリズムで署名されたトークンを受け入れてしまう不備にあり、これを突かれると管理者アカウントが侵害され、システムの完全な制御を奪われる恐れがある。WSO2製品は銀行、政府機関、通信、物流など幅広い業界で採用されており、影響を受ける顧客基盤は世界で約1,000組織に上るという。

CVE-2026-71362はAdobe Commerce(Magento)の認可不備の脆弱性で、CVSSスコアは9.1。攻撃者は既存アカウントを持たず、管理者権限もユーザーの操作も必要とせずに、あるカスタマーセッションを別の顧客アカウントへ切り替えることが可能になる。これにより被害者のアカウントや個人情報に不正アクセスできてしまう。セキュリティ企業Sansecは2026年8月時点で悪用の試みをブロックしたと報告しており、Previdianのテレメトリでは9月10日にオーストラリアの単一IPアドレスからの攻撃試行が確認されている。

## SharePointとMikrotik RouterOSも標的に

CVE-2026-65660はMicrosoft SharePoint Server 2016、2019、およびSubscription Editionに影響するコードインジェクションの脆弱性で、CVSSスコアは8.8。認証済みの低権限ユーザーであっても、リモートで任意のコードを実行できてしまう点が問題となっている。

CVE-2026-67279はMikrotik RouterOSのSSHプロトコルに存在する脆弱性で、CVSSスコアは6.9と他の3件に比べると低いものの、未認証の攻撃者が通常の認証フローを回避してセッションチャネルを開き、コマンドを実行できてしまう。単体でもデバイス上のファイルの作成・改ざんが可能だが、別の脆弱性CVE-2026-86060と組み合わせる「MikroTrick」と呼ばれる攻撃チェーンにより、認証なしで管理者権限を完全に奪取できることが確認されている。インターネットに公開されたRouterOSデバイスへの実際の悪用は9月2日から観測されているという。

## 影響と対応

今回KEVに追加された4件はいずれも、認証やユーザー操作の壁を比較的容易に突破できる点で共通しており、公開サーバーやネットワーク機器を狙う攻撃者にとって魅力的な標的となっている。連邦機関には期限内のパッチ適用が義務付けられているが、CISAは民間組織を含む全ての組織に対しても、KEVカタログに掲載された脆弱性への対応を最優先で進めるよう呼びかけている。該当製品を利用する組織は、ベンダーが提供する修正版への更新に加え、侵害の痕跡がないか早急に確認することが求められる。
