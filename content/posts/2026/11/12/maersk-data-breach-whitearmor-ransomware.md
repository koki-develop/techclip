---
date: "2026-11-12T18:09:40+09:00"
title: "Maersk、買収企業の旧システムから100GBのデータ流出 WhiteArmorが500万ドルを要求"
description: "海運大手MaerskがLF Logisticsの旧システムから不正アクセスを受けたことを確認し、ランサムウェア集団WhiteArmorは約100GBのデータ窃取を主張して500万ドルの支払いを要求している。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/maersk-confirms-data-breach-as-whitearmor-ransomware-demands-5-million/"
  - "https://www.securityweek.com/maersk-confirms-data-theft-amid-5-million-extortion-attempt/"
  - "https://securityaffairs.com/202869/data-breach/whitearmor-demands-5-million-from-maersk-claims-theft-of-100gb-of-data.html"
---

## 概要

海運大手のMaerskは、2022年に買収した香港の物流会社LF Logisticsから引き継いだローカルの旧システムで、不正アクセスによるデータ窃取が発生したことを確認した。ランサムウェア集団WhiteArmorは11月7日にリークサイトでMaerskを標的として公表し、約100GBのデータを窃取したと主張、ビットコインで500万ドルを30日以内に支払うよう要求している。Maerskは侵害を「ローカルの旧システムに隔離されたもの」と位置づけ、中核システムや顧客・取引先とのAPI・EDI連携への影響はないとしている。

## 窃取されたとされるデータの内容

WhiteArmorが主張する流出データには、ドライバー約3万件分のレコード(うち1万6,000件超が平文のパスワードを含む)、1万6,000件超のスタッフアカウント(うち33件はSUPER_ADMIN権限を持つ最高権限アカウント)、署名済みの配送受領書、購入注文を含む1,440万行の在庫レコード、電話番号・メールアドレス・IMEI識別子を含む2万7,842件のモバイル端末ログなどが含まれるとされる。WhiteArmorはこれらの詳細な一覧を公開することで、攻撃の信頼性を高め、Maerskに支払いを迫る圧力材料としている。ただし、これらのデータ内容はあくまで攻撃者側の主張であり、Maerskや第三者による独立した検証はまだ行われていない。

## 攻撃者の手口と要求

WhiteArmorは「500万ドルは(物流部門の)EBITDAのわずか4時間分に相当する」と説明し、Maerskの事業規模の大きさを引き合いに出して支払いを正当化しようとしている。侵入経路や侵害が発生した時期についてはMaersk側から明らかにされておらず、調査は継続中で、必要と判断された場合にのみ影響を受けた関係者に通知するとしている。

## Maerskの対応と今後の見通し

Maerskは「調査の結果は、機密データが開示されていないことを強く示唆している」と説明し、該当システムを隔離した上で他のプラットフォームや顧客・取引先との連携システムへの影響はないと確認したとしている。通常の予約業務などの事業運営に支障は生じないとしている。Maerskにとっては2017年のNotPetyaランサムウェア被害(サーバー4,000台、ワークステーション4万5,000台の再構築を要し、被害額は約3億ドルに達した)に続く大規模なセキュリティインシデントであり、買収企業から引き継いだ旧システムが新たな攻撃対象となるリスクを改めて浮き立たせている。
