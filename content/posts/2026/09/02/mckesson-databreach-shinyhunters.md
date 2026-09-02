---
date: "2026-09-02T18:15:23+09:00"
title: "McKessonにShinyHuntersが侵入、患者データ2億8400万件流出主張と5500万ドルの身代金要求"
description: "米医薬品卸最大手McKessonがボイスフィッシングを起点としたOkta・Salesforce・Snowflakeへの不正アクセスを受け、ハッカー集団ShinyHuntersが患者記録2億8400万件の窃取と約5500万ドルの身代金を主張している。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/mckesson-discloses-breach-after-shinyhunters-claims-patient-data-theft/"
  - "https://techcrunch.com/2026/08/31/hackers-claim-millions-of-patient-records-stolen-during-data-breach-at-healthcare-giant-mckesson/"
  - "https://www.helpnetsecurity.com/2026/08/31/healthcare-company-mckesson-data-breach/"
---

## 概要

米国最大級の医薬品卸売企業McKessonが、ハッカー集団ShinyHuntersによるサイバー攻撃を受けたことを明らかにした。McKessonは8月25日に不正アクセスを検知したとしており、ShinyHuntersは8月21日から25日までの4日間でクラウド環境から約1テラバイトのデータ、患者データベースの行数にして約2億8400万件分を窃取したと主張している。同グループは約5523万6150ドルという極めて具体的な金額の身代金を要求し、72時間の回答期限を設けたが、McKessonはこれに応じていないとみられる。ShinyHuntersは過去2年間で最も活発なデータ恐喝集団の一つとされ、今回の事案は2026年に相次ぐ医療業界へのサイバー攻撃の一つに数えられる。

## 侵入の手口

複数の報道によると、ShinyHuntersはボイスフィッシング（vishing）を起点とした多段階の手法でMcKessonに侵入した。攻撃者はまず「mckesson.claims」というMcKessonのヘルプデスクやIT部門を装ったなりすましドメインを用意し、電話で従業員を騙して認証情報を聞き出したとされる。この手口で複数の従業員のOktaシングルサインオンアカウントを乗っ取ることに成功し、そこを足がかりに社内のSalesforceおよびSnowflake環境へ横展開した。報道では、Salesforce環境は完全に掌握され、Snowflakeからは大量のレコードが抽出されたとしている。このソーシャルエンジニアリング主導の侵入経路は、近年ShinyHuntersが関与したとされる一連のSalesforce・Snowflake関連の大規模侵害と共通する特徴を持つ。

## 流出したデータの範囲

ShinyHuntersが主張する流出データには、患者の氏名、住所、生年月日、社会保障番号、患者ID、メディケイド情報、医療記録番号に加え、診断名、処方薬、アレルギー情報といった臨床データも含まれるという。さらに従業員の自宅住所や社内の内部コミュニケーションも含まれると主張されている。特に影響が大きいとされるのは腫瘍領域・多専門分野（Oncology & Multispecialty）、メディカル・サージカル（Medical-Surgical、医療・外科用品卸）の各事業部門で、これらの顧客データが標的にされた。ただし「2億8400万件」という数字はユニークな患者数ではなくデータベースの行数を指すとみられ、実際に影響を受ける個人数は今後の調査で精査される見込みである。

## 企業の対応と今後の見通し

McKessonは証券取引委員会(SEC)へのForm 8-K提出および顧客向け通知を通じて侵害を公表し、詳細情報は自社ウェブサイトで確認できるとしている。同社幹部は調査がまだ初期段階にあるとしつつ、外部の専門家と連携してシステム監視を継続しており、現時点で進行中の不正アクセスは確認されていないと説明している。一部インシデントに伴うサービスの断続的な遅延が生じているとしているが、全事業ラインでの営業は継続中だとしている。McKessonは影響を受けた個人の具体的な人数や身代金要求への対応方針は明らかにしていない。今回の事案は、Boston ScientificやAbbott Laboratoriesなど2026年に相次いだ医療業界を狙った攻撃の流れに位置づけられ、機密性の高い医療データを狙ったクラウド環境への侵入とソーシャルエンジニアリングを組み合わせた攻撃が今後も続く可能性が指摘されている。
