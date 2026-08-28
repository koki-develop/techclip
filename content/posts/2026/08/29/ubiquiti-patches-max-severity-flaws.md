---
date: "2026-08-29T08:09:51+09:00"
title: "UbiquitiがUniFi製品群の脆弱性22件を修正、うち3件はCVSS満点の10.0"
description: "UbiquitiがUniFi Protect・UniFi OS・UniFi Talkに存在する脆弱性22件を修正し、うち3件はCVSS 10.0の最大深刻度と評価された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/ubiquiti-patches-three-max-severity-security-vulnerabilities/"
  - "https://cyberscoop.com/ubiquiti-unifi-critical-vulnerabilities-patched/"
---

## 概要

Ubiquitiは8月26日、セキュリティ勧告SAB-067を公開し、UniFi Protect・UniFi OS・UniFi Talkにまたがる計22件の脆弱性を修正した。このうち21件が深刻度9.0以上の「クリティカル」、1件が「高」に分類され、さらに3件はCVSSスコアが満点の10.0という最大深刻度に達している。Ubiquitiは今年に入ってから既に3件の10.0評価の脆弱性を公表しており（3月・5月・7月にそれぞれ1件）、今回の3件はそれと同数に達する規模となった。同社は勧告を通じてパッチ情報と対応策を示したものの、悪用が実際に観測されていたかどうかについては言及していない。

## 最大深刻度の3脆弱性

CVSS 10.0と評価されたのはCVE-2026-77537、CVE-2026-77550、CVE-2026-77554の3件。報道によって脆弱性の性質の説明にはやや幅があり、CyberScoopは3件とも「不適切なアクセス制御」による権限昇格の欠陥と位置づける一方、BleepingComputerはより詳細な内訳として、UniFi Protect ApplicationのCVE-2026-77537を不適切な入力検証に起因し未認証の攻撃者が未パッチ端末を侵害できる欠陥、UniFi OSデバイスのCVE-2026-77550をCRLFインジェクションによる認証バイパス、UniFi Talk ApplicationのVoIPシステムに存在するCVE-2026-77554を入力検証不備に起因するコマンドインジェクションと説明している。3件ともユーザーの操作を必要としない低複雑度の攻撃で成立する点が共通しており、悪用のハードルが低いことが懸念材料となっている。

## 影響範囲と対応

修正版はUniFi Protect Applicationがバージョン7.2.105以降、UniFi Talk Applicationがバージョン5.3.2以降で、UniFi OS Serverはバージョン5.1.21以前が脆弱とされる。UniFi製品はネットワーク機器やカメラ、VoIPシステムとして家庭・企業双方で広く利用されており、セキュリティ企業Censysの調査ではインターネット上に露出したUniFi OSインスタンスが10万件以上確認されているが、そのうち今回の脆弱性の影響を受ける台数は明らかになっていない。

Ubiquiti製品を巡っては過去にも国家支援型の攻撃グループやサイバー犯罪者によってボットネット構築に悪用された事例があり、米サイバーセキュリティ・インフラセキュリティ庁(CISA)は今年6月にもUbiquiti関連の脆弱性3件を既知悪用脆弱性(KEV)カタログに追加している。これらは1カ月前にパッチが提供されていたにもかかわらず実際に悪用されていたもので、連邦政府機関には3日以内の是正が義務付けられ、BishopFoxはこれらの脆弱性を連鎖させることで昇格した権限でのリモートコード実行が可能になると実証している。今回の3件についても速やかなパッチ適用が強く推奨される。
