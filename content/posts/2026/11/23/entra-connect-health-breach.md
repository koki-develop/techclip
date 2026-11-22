---
date: "2026-11-23T08:07:21+09:00"
title: "Microsoft Entra Connect Healthの脆弱性が悪用され、管理者メールやテナント情報が流出"
description: "Microsoft Entra Connect HealthのAPIに存在した脆弱性が悪用され、管理者の連絡先情報やテナントのメタデータが読み取り専用で不正に取得された。"
tags:
  - Security
  - Cloud
references:
  - "https://www.bleepingcomputer.com/news/security/microsoft-entra-connect-health-flaw-exploited-to-steal-tenant-data/"
  - "https://www.neowin.net/news/after-outage-microsoft-confirms-another-july-bug-that-led-to-entra-data-breach/"
  - "https://cybersecuritynews.com/microsoft-entra-connect-health-flaw/"
---

## 概要

Microsoftは、クラウド監視サービス「Entra Connect Health」のAPIに存在した脆弱性が攻撃者に悪用され、複数テナントの管理者連絡先情報や組織設定データが不正に取得されたことを確認した。同社によると、取得されたのはあくまで「テナントレベルのメタデータへの読み取り専用アクセス」であり、設定変更の形跡は確認されていないという。パスワード、認証トークン、暗号鍵、オンプレミスのActive Directoryサーバー構成といった機密性の高い情報は流出していないとされる。

## 流出した情報とタイムライン

今回流出が確認されたのは、管理者および技術担当者のメールアドレス、テナントID、表示名、初期ドメイン、国・地域コード、Entraのライセンス階層、ディレクトリ同期の状況やスケジューリング情報などだ。さらに、2024年に廃止された監視エージェント登録用の、すでに期限切れとなった証明書も含まれていたという。Microsoftの説明によれば、脆弱性自体は7月23日に導入され、11月9日に発見、11月19日にサーバー側で修正が適用され、翌11月20日に調査チームが不正アクセスの事実を確認し、同日中に影響を受けた組織への通知が行われた。ただし、実際にいつから悪用が始まっていたのか、何件のテナントが影響を受けたのか、攻撃者の正体については明らかにされていない。

## Microsoftの対応と今後の注意点

修正はクラウド側のサーバーに適用されたため、顧客側でのソフトウェア更新作業は不要とされる。Microsoftは影響を受けた、あるいは影響を受けた可能性のある組織に対し、フィッシング耐性のある多要素認証の導入、Privileged Identity Management(PIM)の活用、EntraおよびAzureの操作ログを確認し不審な管理者アクティビティがないか点検することを推奨している。流出した情報自体は資格情報ではないものの、管理者のメールアドレスやテナント構成情報は標的型フィッシングや偵察活動に利用されるおそれがあり、注意が必要だ。

今回の一件は、Microsoftが直近のEntraの大規模アウテージ(障害)の原因究明を進めている最中に明らかになったもので、クラウドIDサービスの運用基盤における脆弱性管理の難しさを改めて浮き立たせる結果となった。公開から発見まで3ヶ月以上の期間が空いていたことも踏まえ、今後は同種のAPIに対する監査体制の強化が求められそうだ。
