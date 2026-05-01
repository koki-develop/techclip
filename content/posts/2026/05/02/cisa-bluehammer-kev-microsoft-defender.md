---
date: "2026-05-02T02:27:28+09:00"
title: "CISAがMicrosoft DefenderのゼロデイCVE-2026-33825をKEVに追加、連邦機関に5月7日までのパッチ適用を命令"
description: "CISAはMicrosoft Defenderの権限昇格ゼロデイ脆弱性「BlueHammer」（CVE-2026-33825）を既知悪用脆弱性カタログに追加し、連邦機関に2026年5月7日までのパッチ適用を義務付けた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/cisa-orders-feds-to-patch-microsoft-defender-flaw-exploited-in-zero-day-attacks/"
---

## 概要

米サイバーセキュリティ・インフラセキュリティ庁（CISA）は、Microsoft Defenderに存在する高深刻度の権限昇格ゼロデイ脆弱性「BlueHammer」（CVE-2026-33825）を既知悪用脆弱性（KEV）カタログに追加した。これに伴い、連邦民間行政機関（FCEB）に対して2026年5月7日までのパッチ適用を命令した。Microsoftはすでに2026年4月14日の月例パッチ（Patch Tuesday）でこの脆弱性を修正済みだが、実際の攻撃での悪用が確認されていることから、CISAが迅速な対応を求めた形となる。

## 脆弱性の詳細とPoC公開の経緯

CVE-2026-33825は、Microsoft Defenderに存在する権限昇格の脆弱性で、低権限のローカルユーザーがSYSTEM権限を取得できる。脆弱性のPoCコードは、セキュリティ研究者「Chaotic Eclipse」がMicrosoft Security Response Center（MSRC）の対応に不満を示し、4月7日に意図的に公開したものだ。このPoC公開と同時に、「RedSun」および「UnDefend」という2件の追加脆弱性も開示されている。MSRCの対応への抗議という形でのPoC公開は、研究者コミュニティとベンダー間の情報開示をめぐる緊張関係を改めて浮き彫りにした。

## 攻撃の実態と影響範囲

実際の攻撃では「hands-on-keyboard」型のアクターによる活動が報告されており、ロシアからのFortiGate SSL VPNアクセスを含む、より広範なシステム侵害の一部としてこの脆弱性が悪用されている。ローカル権限昇格として分類されるものの、既存の侵害経路と組み合わせることで攻撃者がシステム全体の制御を奪う手段となっており、実害の深刻さはCVSSスコアが示す以上に大きい。連邦機関に限らず、Windows環境を持つ民間組織も早急なパッチ適用が推奨される。

## 対応策

Microsoftは2026年4月14日のPatch Tuesdayで修正パッチをリリース済みであるため、Windows Updateを通じて最新の更新プログラムを適用することで対処できる。CISAのKEVカタログへの追加は連邦機関への法的拘束力を伴う指令であるが、民間企業に対してもパッチ適用の優先度を高める指針となる。組織のセキュリティチームは、パッチ状況の確認とともに、ネットワーク上での不審な権限昇格の痕跡がないかログを精査することが推奨される。
