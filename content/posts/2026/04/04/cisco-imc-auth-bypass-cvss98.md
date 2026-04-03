---
date: "2026-04-04T02:16:45+09:00"
title: "CiscoがIMCのCVSS 9.8認証バイパス脆弱性（CVE-2026-20093）を修正、管理者パスワード変更が無認証で可能に"
description: "CiscoはIntegrated Management Controller（IMC）に存在するCVSSスコア9.8の重大な認証バイパス脆弱性CVE-2026-20093を修正するパッチを公開した。未認証のリモート攻撃者が管理者を含む任意ユーザーのパスワードを変更し、システムへのフルアクセスを取得できる。"
tags:
  - Security
references:
  - "https://www.securityweek.com/"
  - "https://thehackernews.com/2026/04/cisco-patches-98-cvss-imc-and-ssm-flaws.html"
  - "https://www.bleepingcomputer.com/news/security/critical-cisco-imc-auth-bypass-gives-attackers-admin-access/"
  - "https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-cimc-auth-bypass-AgG2BxTn"
---

## 概要

Ciscoは2026年4月1〜2日、Integrated Management Controller（IMC）にCVSSベーススコア9.8の重大な認証バイパス脆弱性（CVE-2026-20093）が存在することを公表し、対処するパッチをリリースした。CVSSベクター `CVSS:3.1/AV:N/AC:L/PR:N/UI:N/S:U/C:H/I:H/A:H` が示す通り、ネットワーク越しに低い攻撃複雑度で、認証も利用者操作も不要で悪用できる最高水準の危険度を持つ。

脆弱性はIMCのウェブ管理インターフェースにおけるパスワード変更リクエストの**不適切な入力検証（CWE-20）**に起因する。攻撃者は細工したHTTPリクエストを送信するだけで認証を完全に回避し、管理者アカウントを含む任意ユーザーのパスワードを変更した上でシステムへのフルアクセスを取得できる。Ciscoは公式声明で「攻撃者は認証をバイパスし、管理者ユーザーを含むシステム上の任意ユーザーのパスワードを変更してそのユーザーとしてシステムへアクセスできる」と述べている。

## なぜ特に危険なのか

IMC（別名CIMC）はHPのiLOやDellのiDRACに相当するCiscoのアウトオブバンドサーバー管理コントローラーである。ホストOSとは独立して動作するため、サーバーOSの電源がオフの状態でも攻撃が成立する。このレイヤーを侵害された場合、EDRやSIEM、OSレベルのセキュリティ対策はほぼ無力化され、ハードウェアへの永続的かつ深いアクセスを攻撃者に与えることになる。

SOCRadarのCISOであるEnsar Seker氏は「このレベルでの認証バイパスは、攻撃者にハードウェア自体の完全な管理権限を渡すことに等しい」とコメントしている。過去にはHPE iLOを標的としたiLOBleedインプラント（2022年）やIPMIインターフェースを狙ったJungleSecランサムウェア（2018年）など、アウトオブバンド管理インターフェースへの攻撃が現実の被害を生じさせた前例がある。

## 影響を受ける製品とパッチバージョン

以下の製品が影響を受ける（括弧内は修正済みバージョン）：

- **5000シリーズ ENCS（Enterprise Network Compute Systems）** — 4.15.5以降
- **Catalyst 8300シリーズ Edge uCPE** — 4.18.3以降
- **UCS C-Series M5・M6ラックサーバー（スタンドアロンモード）** — 4.3(2.260007)、4.3(6.260017)、または6.0(1.250174)以降
- **UCS E-Series M3サーバー** — 3.2.17以降
- **UCS E-Series M6サーバー** — 4.15.3以降

また、UCS C-Seriesハードウェアをベースとした以下のCiscoアプライアンスも影響を受ける：Application Policy Infrastructure Controller（APIC）サーバー、Cyber Vision Centerアプライアンス、Secure Firewall Management Centerアプライアンス、Malware Analyticsアプライアンス。

## 対応と推奨事項

Ciscoはこの脆弱性に対して**ワークアラウンドは存在しない**と明言しており、唯一の対策はパッチ適用済みバージョンへのアップグレードである。ネットワークレベルの緩和策も効果がないとされるため、影響を受ける製品を利用している組織は即時のアップグレードが強く推奨される。

なお、同じCiscoのアドバイザリ群では、Cisco Smart Software Manager（SSM）On-Premにも同じくCVSS 9.8のCVE-2026-20160が修正されており、こちらは未認証のリモートコード実行が可能な内部API露出に起因する。現時点では野生での悪用やPoC公開の報告はないが、Cisco脆弱性の迅速な武器化という過去の傾向から、Cisco PSIRTは即時パッチ適用を強く勧告している。本脆弱性はセキュリティ研究者「jyh」によって発見・報告された。
