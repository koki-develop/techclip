---
date: "2026-08-04T02:31:34+09:00"
title: "英国警察の法的データベースPNLDが侵害、ExfilSquadが13万件超の連絡先情報を窃取・公開"
description: "英国警察向け法的データベースPNLDがハッカー集団ExfilSquadの侵害を受け、警察官や刑事司法関係者ら13万件以上の連絡先情報がダークウェブ上に公開された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/exfilsquad-hackers-leak-info-of-over-100-000-uk-police-officers-staff/"
  - "https://www.theregister.com/cyber-crime/2026/08/03/police-national-legal-database-confirms-data-theft-after-dark-web-leak/5282332"
  - "https://thehackernews.com/2026/08/pnld-breach-exposes-uk-police-and.html"
---

## 概要

英国警察向けの法的データベースサービス「Police National Legal Database(PNLD)」がサイバー攻撃を受け、警察官や刑事司法関係者ら13万人以上の連絡先情報が窃取・公開されたことが明らかになった。PNLDはイングランドとウェールズの内務省管轄43警察組織および英国鉄道警察が利用する法的情報提供サービスで、一般向けの法律相談サイト「Ask the Police」も運営している。侵害は2026年7月26日に発覚し、攻撃を仕掛けたと主張するデータ恐喝集団「ExfilSquad」がダークウェブ上のリークサイトにPNLDを掲載したことで表面化した。

窃取されたデータは、PNLD利用者である警察官・職員の氏名、所属組織、業務用メールアドレスなど約11万4000件と、Ask the Police利用者(一般市民)の氏名・メールアドレス約2万1000件を合わせた計約13万5000件、容量にして1.9GBに上るとされる。ExfilSquad側は当初「13万5000件の法執行機関関係者データ」を窃取したと主張していたが、PNLDは2025-26年次報告でサービスの登録ユーザー数を108,429件としているが、被害件数の正確な内訳については明言していない。PNLDは、パスワードやセキュリティ認証情報、被害者・証人情報、被疑者記録などは一切侵害されていないと説明している。

## 対応状況

PNLDは影響を受けた組織に対し、事案発覚後速やかに連絡し詳細な情報とガイダンスを提供したとしている。北東地域組織犯罪対策ユニット(North East Regional Organised Crime Unit)によれば、身代金要求は受け取っていないという。捜査には国家犯罪対策庁(NCA)やサイバーセキュリティ専門家の協力を得ているほか、情報コミッショナー事務局(ICO)にも通知済みである。なお、PNLDは本件をExfilSquadによる犯行と公式には断定していない。

## 技術的な背景

侵害の具体的な原因は公式には明らかにされていないが、一部の研究者はPNLDがMicrosoft Power Platform技術を利用している点に着目し、Power PagesポータルにおいてDataverseテーブルへの匿名ユーザーアクセスが広範囲に許可される設定ミスがあった可能性を指摘している。ランサムウェアやマルウェア、既知の脆弱性の悪用を示す確証は現時点で確認されておらず、根本原因は未確定のままとなっている。

ExfilSquadは以前にも半導体大手Analog Devicesや英教育省(Department for Education)を標的にしたとされる恐喝集団で、今回のPNLD侵害とほぼ同時期にも教育省からも約60万件のデータを窃取したと主張していた。同グループはさらにMicrosoftを被害者として名乗り、13GB相当のデータを保有していると主張しているが、この件についても真偽は確認されていない。

## 今後の展望

窃取されたデータには対象者の氏名や業務用連絡先が含まれるため、フィッシングやなりすましなど二次被害のリスクが懸念される。PNLDやICO、NCAによる調査が続く中、侵害の正確な原因究明と、Microsoft Power Platformを利用する他の公共機関における同様の設定ミスの有無が今後の焦点となる見込みだ。
