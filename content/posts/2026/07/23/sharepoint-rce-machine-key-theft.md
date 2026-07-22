---
date: "2026-07-23T02:32:22+09:00"
title: "SharePoint重大脆弱性CVE-2026-50522が実悪用、マシンキー窃取でパッチ後も侵害継続の恐れ"
description: "オンプレミスSharePoint ServerのRCE脆弱性CVE-2026-50522(CVSS 9.8)が公開PoC直後から実際に悪用され、IISマシンキー窃取による長期侵害が確認された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/critical-sharepoint-rce-flaw-exploited-to-steal-machine-keys/"
  - "https://thehackernews.com/2026/07/critical-sharepoint-rce-cve-2026-50522.html"
  - "https://www.helpnetsecurity.com/2026/07/22/sharepoint-cve-2026-50522-exploited/"
---

## 概要

オンプレミス版Microsoft SharePoint Serverに存在する重大なリモートコード実行(RCE)脆弱性「CVE-2026-50522」(CVSSスコア9.8)が、公開された概念実証(PoC)コードの登場直後から実際に悪用されていることが、セキュリティ企業watchTowrの調査で明らかになった。攻撃者は本脆弱性を突いてSharePointサーバーからIISマシンキーを窃取し、正規の認証トークンを偽造することで、脆弱性そのものにパッチを適用した後も長期的にシステムへアクセスし続ける手口を確立している。影響を受けるのはSharePoint Subscription Edition、2019、2016の自己管理(セルフホスト)環境で、インターネットに公開された対象インスタンスは世界で約1,500件、その多くが米国に所在するとみられる。

## 技術的な詳細

この脆弱性は、信頼できないデータのデシリアライズに起因する欠陥で、SharePointのサインインエンドポイント(`/_trust/default.aspx`)を狙い、WS-Federationのサインイン応答内に偽造した`SecurityContextToken`としてCookie形式で悪意ある.NET `BinaryFormatter`ペイロードを送り込むことで成立する。Microsoft側は本来Site Owner権限での認証を前提とした脆弱性として分類していたが、セキュリティ企業Defused Cyberの分析によれば、実際に観測された攻撃リクエストには認証情報が一切含まれておらず、攻撃者が何らかの手法で認証要件を回避し、事実上「認証不要」の形で悪用していることが示唆されている。Microsoftは本脆弱性を攻撃複雑度「低(AC:L)」、悪用可能性「Exploitation More Likely」と評価しており、攻撃者が高度な事前知識を持たずとも再現性高く攻撃を成功させられる状態にあるとしている。

攻撃はSharePointからマシンキーを1回のリクエストで窃取する手口が確認されており、盗まれたマシンキーがあれば攻撃者はパッチ適用後も正規の認証トークンを偽造してシステムへの侵入を継続できてしまう点が最大の脅威となっている。

## 発覚の経緯

セキュリティ企業Defused Cyberは7月17日、SharePoint内の未文書化のデシリアライズ経路を検知し、早期の警告を発していた。7月20日にはwatchTowrがPoCコードの存在を確認し、同社のグローバルハニーポットネットワーク「Attacker Eye」が、PoC公開からわずか数時間のうちに実際の悪用試行を捕捉したという。公開PoCは研究者Janggggg氏がGitHub上でPowerShellによるデモンストレーション用エクスプロイトとして公開したものとされる。なお本件は、2026年7月にオンプレミスSharePoint Serverで実悪用が確認された脆弱性としては、CVE-2026-56164、CVE-2026-58644に続く3件目となる。

## 推奨される対策

watchTowrやCISAなど複数の専門家・機関は、パッチ適用だけでは不十分であると強く警告している。CISAは「侵害の痕跡を捜索・修復してからIISマシンキーをローテーションすべき」と助言しており、単に脆弱性を修正するだけでなく、既に侵害を受けている可能性を前提とした対応が求められる。具体的な推奨事項としては、(1) Microsoftが7月に公開したセキュリティ更新プログラムを直ちに適用すること、(2) 侵害の兆候がないか事前に調査すること、(3) その上でIISマシンキーをローテーションすること、(4) SharePoint Webアプリケーションに対してAMSI(アンチマルウェア スキャン インターフェース)連携を有効化すること、が挙げられている。パッチ適用のみでは既に窃取されたマシンキーによる不正アクセスを防げないため、資格情報のローテーションを含めた包括的な対応が急務となっている。
