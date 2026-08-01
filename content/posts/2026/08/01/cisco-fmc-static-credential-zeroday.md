---
date: "2026-08-01T20:25:53+09:00"
title: "Cisco FMCに組み込み静的認証情報の脆弱性、実際のゼロデイ攻撃で悪用中"
description: "Cisco Secure Firewall Management Centerに低権限アカウントの静的認証情報がハードコードされていた脆弱性CVE-2026-20316が、実際のゼロデイ攻撃で悪用されていることが判明し、CISAも既知の悪用脆弱性カタログに追加した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/cisco-warns-of-fmc-static-credential-flaw-exploited-in-zero-day-attacks/"
  - "https://thehackernews.com/2026/07/cisco-fmc-zero-day-actively-exploited.html"
  - "https://www.securityweek.com/cisco-secure-fmc-zero-day-exploited-in-the-wild/"
---

## 概要

Ciscoは、Secure Firewall Management Center(FMC)ソフトウェアに低権限アカウント向けの静的認証情報がハードコードされていた脆弱性(CVE-2026-20316)が、実際のゼロデイ攻撃で悪用されていると警告した。この脆弱性を悪用すると、認証されていない遠隔の攻撃者がこの組み込みアカウントを使ってログインし、そのアカウントがアクセス可能な機密データを取得できる。CVSSスコア自体は5.3と中程度だが、他のFMCの脆弱性と組み合わせることで管理者権限への昇格が可能なため、Ciscoは深刻度を「High」に引き上げて評価している。CISAは7月29日付でこの脆弱性を「既知の悪用脆弱性(KEV)」カタログに追加し、連邦機関に対して8月1日までのパッチ適用を義務付けた。

## 影響範囲と技術的な詳細

影響を受けるのはCisco Secure FMC Softwareのバージョン7.0、7.2、7.4、7.6、7.7、10.0で、それぞれに対応するホットフィックスが提供されている(例:バージョン7.0向けの`Cisco_Firepower_Mgmt_Center_Hotfix_GB-7.0.9.1-3.sh.REL.tar`)。一方、クラウド提供型のFMC(Cloud-Delivered FMC)、Firewall Device Manager、ASA Software、Threat Defense Software、Security Cloud Controlは影響を受けない。この脆弱性はHorizon3.aiの研究者Jimi Sebree氏が報告したもので、同社は現時点で技術的な詳細は公表していない。侵害の兆候としては、エキスパートモードで`cat /var/log/messages | grep license`を実行し、ログ中に`/var/tmp/license.tmp`という文字列が含まれていないかを確認する方法が有効とされている。

## 対応策と今後の見通し

Ciscoは有効な回避策(ワークアラウンド)は存在しないとしており、公開済みのホットフィックスを直ちに適用するよう強く推奨している。すでに侵害された可能性がある場合は、認証情報・鍵・証明書をすべてローテーションし、復旧作業についてはCisco TAC(Technical Assistance Center)に連絡するよう案内している。また、FMCの管理インターフェースをインターネットに公開しないよう構成することで、攻撃対象領域を大幅に縮小できるとも説明している。Ciscoは攻撃者の正体や攻撃を受けた組織、攻撃開始時期などの詳細は明らかにしていないが、実際の攻撃で悪用が確認されている以上、該当バージョンを利用する組織は速やかな対応が求められる。
