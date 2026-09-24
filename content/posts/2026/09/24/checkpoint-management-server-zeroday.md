---
date: "2026-09-24T18:14:56+09:00"
title: "Check Point管理サーバーにCVSS 9.8の深刻な脆弱性、7月から標的型攻撃で悪用と判明"
description: "Check PointがSecurity Management Serverの認証不要パストラバーサル脆弱性CVE-2026-93616を修正、7月から標的型攻撃で悪用されていたことが判明した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/check-point-warns-of-management-server.html"
  - "https://www.bleepingcomputer.com/news/security/check-point-patches-management-server-zero-day-exploited-in-attacks/"
  - "https://www.securityweek.com/check-point-patches-exploited-management-server-zero-day/"
---

## 概要

Check Pointは、Security Management Serverのウェブサービスに存在する認証前パストラバーサル脆弱性(CVE-2026-93616、CVSS 9.8)を公開し、修正パッチをリリースした。攻撃者は認証なしにサーバーのウェブサービスへアクセスできれば任意のスクリプトをアップロードして実行できるといい、深刻度・攻撃容易性ともに最高レベルに位置づけられる。この脆弱性は今回の公開に先立つ7月23日から標的型攻撃で既に悪用されていたことが判明しており、Check Pointは自社が把握する範囲で「一部の顧客が実際に攻撃を受けた」ことを認めている。米CISAは9月23日、本脆弱性を既知の悪用済み脆弱性(KEV)カタログに追加した。

## 脆弱性の詳細

CVE-2026-93616は、Security Management Server、Multi-Domain Security Management Server、Log Server、Multi-Domain Log Server、SmartEventといった複数の製品にまたがるディレクトリトラバーサル兼ファイルアップロードの欠陥で、中央でセキュリティポリシーを管理し管理者の変更処理やログ収集を担うこれらのサーバーの性質上、侵害された場合の影響範囲は大きい。影響を受けるバージョンはR82.20(未パッチ)、R82.10(Jumbo Hotfix Take 44以下)、R82(同Take 126以下)、R81.20(同Take 166以下)、およびサポート終了済みのR81.10(同Take 190以下)、R81、R80系列全般と広範に及ぶ。Check PointはR82.20向けのSecurity Hotfixに加え、R82.10(Take 45)、R82(Take 127)、R81.20(Take 170)、R81.10(Take 192)向けのJumbo Hotfix Accumulatorを提供したが、通常のLivePatch更新ではこの脆弱性は解消されない点に注意が必要としている。

## 悪用の経緯と関連する脆弱性

タイムラインを追うと、Check Pointは9月9日にVPN証明書検証に関わる別の脆弱性CVE-2026-85102(CVSS 9.8、Security GatewayおよびSparkファイアウォールに影響)を修正しており、その3日後の9月12日にはこのVPN脆弱性を突く悪用試行がSpark顧客を標的に観測されている。攻撃では「CN=vpn,OU=users,O=global」などを含む証明書が使われたという。さらに9月16日には管理サーバー関連の別の脆弱性CVE-2026-91843がLivePatchで修正されており、今回のCVE-2026-93616の悪用開始(7月23日)を含めると、Check Point製品を狙った攻撃キャンペーンが数か月にわたり断続的に展開されていたことになる。CVE-2026-85102についてもCISAのKEVカタログに追加されており、Sparkファイアウォールを狙った悪用は世界規模で確認されている。

## 対応策と影響

Check Pointは管理者に対し、まず自社サーバーのバージョンが影響対象リストに該当するか確認したうえで、サポート技術情報sk1000171に記載されたパッチを速やかに適用するよう呼びかけている。パッチ適用までの暫定策としては、Management Serverをセキュリティゲートウェイやファイアウォールの背後に置き、TCP/19009ポートへのアクセスを信頼できるIPアドレスに限定すること、SmartConsoleへのアクセス制限を行うことなどが挙げられている。また、advisoryで公開されている侵害の痕跡(IoC)を用いて、自組織が既に侵害を受けていないか過去にさかのぼって確認することも推奨されている。CISAのKEV登録を受け、米国の連邦機関には期限内の対応が義務付けられる見通しであり、Check Point製品を利用する企業は自組織のみならずサプライチェーン全体への影響も踏まえた優先度の高い対応が求められる。
