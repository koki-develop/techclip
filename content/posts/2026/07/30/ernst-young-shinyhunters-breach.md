---
date: "2026-07-30T02:30:05+09:00"
title: "会計大手EY、ShinyHuntersが顧客税務データの侵害を主張し7月31日に交渉期限を設定"
description: "恐喝グループShinyHuntersが会計大手Ernst & Youngのシステム侵害と顧客税務データの窃取を主張し、7月31日までの対応を要求している。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/ernst-and-young-data-breach-claimed-by-shinyhunters-extortion-gang/"
  - "https://www.securityweek.com/shinyhunters-claims-ernst-young-hack/"
  - "https://hackread.com/shinyhunters-ernst-young-ey-data-breach-threat-leak/"
---

## 概要

恐喝グループShinyHuntersが7月27日、ダークウェブ上のリークサイトに大手会計事務所Ernst & Young(EY)を追加し、「Yes it was us. Now come talk to us.」と宣言してデータ侵害への関与を主張した。同グループは7月31日までにEYが交渉に応じなければ、窃取したとされるデータを公開すると脅迫している。EYはこの主張について公式なコメントを出しておらず、SecurityWeekやBleepingComputerの取材にも応じていない。両社とも、脅迫グループの主張を独自に検証できていない点を明記している。

## 侵害の経緯とデータの内容

EYは4月23日に異常なアクセスを検知し、調査の結果、税務担当者が利用するサードパーティ製のITサービス管理プラットフォームに対して3月28日から4月12日の間に不正アクセスがあり、複数の文書がダウンロードされていたことが判明したとされる。このプラットフォームで受け付けていたサポートチケットには、顧客の税務申告に関わる個人・金融情報を含む書類が添付されていたという。報じられている流出データの内容としては、顧客の氏名・住所・社会保障番号、金融口座番号、クレジット/デビットカード情報、投資関連情報などが挙げられている。ただし、影響を受けた人数の規模についてEYは明らかにしていない。

なお、ShinyHunters側は追加の主張として、特定されていないサプライチェーン攻撃を通じて入手した認証情報によりEYのJira・GitHub・Microsoft Azure環境にも侵入したとしているが、この部分についても裏付けは取れておらず未検証の情報にとどまる。

## EYの対応と脅威グループの実績

EYはシステムを保護し不正アクセスを排除した上で、連邦法執行機関に通知したとされる。また影響を受けた可能性のある顧客に対しては、Experianを通じて24ヶ月間のクレジット監視および身元回復サービスを無償提供している。

SecurityWeekによれば、ShinyHuntersはこれまでにも University of Nottingham、DentaQuest、7-Eleven、Medtronic、Wynn Resorts、Oracle PeopleSoft、Salesforceなど多数の大手組織への侵害を主張してきた実績があり、脅迫を実行に移す傾向があるグループとして知られている。今回もこのパターンを踏襲する形で7月31日の期限が設定されており、EYが交渉に応じるか、データが実際に公開されるかが今後の焦点となる。
