---
date: "2026-08-17T20:04:55+09:00"
title: "Defenderのパッチ回避PoC「ShieldBreak」公開、SYSTEM権限奪取の成功率100%と報告"
description: "研究者がMicrosoft Defenderの脆弱性CVE-2026-50656に対するパッチを回避する概念実証「ShieldBreak」を公開し、SYSTEM権限への昇格が成功率100%で可能だと報告した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/08/shieldbreak-zero-day-poc-claims.html"
---

## 概要

セキュリティ研究者が8月11日、Microsoft Defenderの脆弱性CVE-2026-50656(通称RoguePlanet、CVSS 7.8)に対するMicrosoftのパッチを回避する概念実証(PoC)「ShieldBreak」を公開した。研究者は「MicrosoftはRoguePlanet脆弱性を適切に修正できていない」と主張しており、Windows 11 25H2(Canaryチャンネル)やWindows Server 2025においてSYSTEM権限への昇格が可能だとしている。PoCの成功率は100%と報告されており、深刻度の高い問題として注目を集めている。研究者はChaotic Eclipse(別名INFINITE NIGHTMARE、MSNightmare、Nightmare-Eclipse)を名乗っており、セキュリティ研究者のKevin Beaumont氏とWill Dormann氏がそれぞれ独立してエクスプロイトの動作を確認したという。

## 技術的な詳細

RoguePlanetは、マルウェア対策エンジンのコアコンポーネントであるmpengine.dll内の競合状態(レースコンディション)を突く脆弱性で、SYSTEM権限への昇格を許すものだった。これに対しShieldBreakは、Defenderのクラウドハイドレーション(cloud-hydration)スキャン中に発生するユーザーモードのコールバックフックを利用する点で、元のRoguePlanetとは異なる手法を採る。具体的には、Cloud Filter API(cfapi)を悪用してファイル内容を操作し、CLFS(Common Log File System)を利用してアイデンティティファイルをすり替え、EICARテストファイルを設置したうえでObject Managerのシンボリックリンクを使う。さらにwer.dllの読み込み機構を通じて攻撃者のコードを仕込んだphoneinfo.dllをロードさせ、最終的にconhost.exeをSYSTEM権限で起動させることで権限昇格を完成させる。なお、研究者は先月、別の脆弱性CVE-2026-62832(CVSS 7.8、通称LegacyHive、Windows User Profile Serviceの権限昇格の欠陥)も開示しており、今回のMicrosoftの月例パッチで修正されている。Windows 10および対応するサーバーエディションも脆弱とされるが、現時点でPoCの対象には含まれていない。

## 経緯と今後の見通し

RoguePlanetは2026年6月に最初に開示され、Microsoftは7月に初回のパッチをリリースした。その後、研究者はデータ漏えいにつながる追加の欠陥を報告し、8月11日にはパッチ回避を実証するShieldBreakを公開するに至った。Microsoftは「報告された脆弱性を認識しており、その正当性と適用範囲について積極的に調査している」との声明を出し、協調的な脆弱性開示への取り組みとタイムリーな更新による顧客保護を強調している。なお、Microsoftは8月の月例パッチで421件のセキュリティ欠陥を修正しており、この中にはSYSTEM権限を要する形で実際に悪用されているWindows Ancillary Function Driverのゼロデイ脆弱性CVE-2026-68820(CVSS 7.0)も含まれる。米CISAは連邦機関に対し、8月25日までに関連するCVE-2026-68820への対応を完了するよう求めている。ShieldBreakの主張が正式に検証されれば、Defenderの防御機構そのものに対する信頼性が問われる事態となりそうで、Microsoftの追加対応の行方が注目される。
