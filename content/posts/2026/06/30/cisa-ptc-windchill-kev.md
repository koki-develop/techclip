---
date: "2026-06-30T02:53:20+09:00"
title: "CISAがPTC Windchill RCE脆弱性CVE-2026-12569をKEVカタログに追加、JSPウェブシェル攻撃が進行中"
description: "CISAはPTC WindchillのRCE脆弱性CVE-2026-12569（CVSS 9.3）をKnown Exploited Vulnerabilitiesカタログに追加し、製造・重要インフラ向けPLMシステムへのJSPウェブシェル展開による実攻撃が確認されていることを警告した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/cisa-adds-exploited-ptc-windchill-rce.html"
  - "https://www.securityweek.com/first-ever-exploitation-of-ptc-windchill-vulnerability-discovered-in-the-wild/"
  - "https://securityaffairs.com/194290/security/u-s-cisa-adds-cisco-and-ptc-windchill-and-flexplm-flaws-to-its-known-exploited-vulnerabilities-catalog.html"
---

## 概要

米国サイバーセキュリティ・インフラセキュリティ庁（CISA）は2026年6月25日、PTC WindchillおよびPTC FlexPLMに存在するリモートコード実行（RCE）脆弱性**CVE-2026-12569**（CVSSスコア 9.3）をKnown Exploited Vulnerabilities（KEV）カタログに追加した。これはPTC製品がKEVカタログに追加された初めての事例であり、製品ライフサイクル管理（PLM）ソフトウェアが実際の攻撃に悪用されている深刻な事態を反映している。連邦政府機関には2026年6月28日を期限として対策の適用が義務付けられ、民間企業にも同カタログの確認と対処が強く推奨されている。

同時に、Cisco Unified Communications Manager（Unified CM）およびUnified CM SMEに影響するSSRF脆弱性**CVE-2026-20230**（CVSS 8.6）もKEVカタログへ追加された。こちらはパブリックなProof-of-Conceptコードが公開されており、実際の悪用も確認されている。

## 脆弱性の技術的詳細

CVE-2026-12569は、PTC Windchill PDMlinkおよびPTC FlexPLMにおける**信頼されないデータのデシリアライゼーション**に起因する不適切な入力検証の欠陥だ。リモートの未認証攻撃者が特殊に細工したリクエストを送信することで任意のコードを実行できる。影響を受けるバージョンは11.0 M030より前のすべてのリリースであり、PTCは2026年6月17日にパッチの提供を開始、翌18日には侵害指標（IoC）を公開した。

攻撃者は脆弱なシステムに対してJSP形式のウェブシェルを展開し、リモートコマンド実行とデータ窃取を可能にする永続的な足がかりを確立している。確認されているウェブシェルのファイルパターンは `/Windchill/login/[0-9a-f]{16}.jsp` であり、ファイルハッシュ `55a1eb4c2d3da04376df39d7ba832569c6af1a37a0cf2b95f754ac898023a30c` も攻撃指標として公開されている。主要なC&Cサーバーアドレスとして `5.180.41.35` が特定されているほか、複数の不審なIPアドレスが観測されている。

## 影響と背景

PTCのWindchillは自動車・航空宇宙・防衛・重工業など製造業の重要インフラで広く採用されているPLMソフトウェアだ。この種のシステムへの侵害は製品設計データや知的財産の窃取、さらにはサプライチェーン攻撃の起点となり得るため、被害の影響範囲は甚大となる可能性がある。ドイツ警察は同脆弱性の悪用が確認される前の段階で関連組織に対して攻撃の差し迫った脅威を警告していたとも報じられており、早期から攻撃者の活動が懸念されていた状況が浮かび上がる。

なお、PTCが別の脆弱性CVE-2026-4681への対応でドイツ当局が動いていた経緯もあり（実際の悪用は未報告）、今回のCVE-2026-12569はPTC製品に対する初の野生での実悪用として記録された。

## 推奨される対策

既存の侵害を確認・封じ込めるために以下の対策が推奨されている。

- コマンド＆コントロールサーバー（`5.180.41.35`）をファイアウォールでブロック
- HTTPサーバーログで `/Windchill/login/*.jsp` へのPOSTリクエストを検索
- ファイルシステム上の16文字の16進数名JSPファイルを調査
- `/tmp` ディレクトリおよびWindchill作業ディレクトリ内の `flst.txt` を確認
- `X-windchill-req:` ヘッダーをブロックするWAF/IDSルールを導入
- ログインエンドポイントへのインターネットからの直接アクセスを制限

PTCのパッチ（バージョン11.0 M030以降）の早急な適用が最優先事項であり、パッチ適用前後の侵害調査も強く推奨される。
