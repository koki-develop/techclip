---
date: "2026-07-10T02:41:08+09:00"
title: "Ubiquiti、UniFi全製品群に及ぶ重大脆弱性7件を修正 最大深刻度CVSS 10.0の未認証コマンドインジェクションも"
description: "UbiquitiがUniFi Connect・Talk・Access・Protect・OSにまたがる重大脆弱性7件を修正した。うち1件はCVSS 10.0の未認証コマンドインジェクションで、インターネットに露出しているUniFi OSインスタンスは10万台以上とされる。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/07/ubiquiti-patches-critical-unifi-flaws.html"
  - "https://www.bleepingcomputer.com/news/security/ubiquiti-warns-of-new-max-severity-unifi-os-vulnerability/"
  - "https://securityaffairs.com/194978/security/ubiquiti-patches-critical-unifi-os-flaws-allowing-command-injection-and-privilege-escalation.html"
---

## 概要

Ubiquitiは、UniFi Connect、UniFi Talk、UniFi Access、UniFi Protect、UniFi OSにまたがる合計7件の重大な脆弱性を修正するセキュリティアップデートを公開した。中でも最も深刻なのはUniFi Connect Applicationに存在するCVE-2026-50746で、CVSSスコアは最大値の10.0。ネットワークにアクセスできる攻撃者が認証なしにホストデバイス上で任意のコマンドを実行できるというもので、UniFi Connectは照明やEV充電器といったビル設備の管理にも利用されているため、影響は物理的なインフラにまで及びうる。セキュリティ調査企業Censysの追跡によれば、インターネットに露出しているUniFi OSインスタンスは10万件以上(うち米国内だけで約5万件)にのぼり、今回のアップデートは広範なデバイス群に関わる。現時点でこれら新規脆弱性が実際の攻撃で悪用されたという報告はないが、Ubiquitiはセキュリティアドバイザリ「Bulletin 066」を通じて全ユーザーに速やかなアップデートを呼びかけている。

## 脆弱性の詳細

修正された7件はいずれもCVSSスコア9.0以上の重大な脆弱性で、脆弱性の種類は多岐にわたる。最大深刻度のCVE-2026-50746(CVSS 10.0、UniFi Connect Application v3.4.16以前)は前述の通り未認証コマンドインジェクションだ。UniFi Talk(v5.1.2以前)にはSQLインジェクションによる権限昇格を許すCVE-2026-50747(CVSS 9.9)が存在する。UniFi Access(v4.2.28以前)には入力値検証の不備であるCVE-2026-50748(CVSS 9.9)と、アクセス制御不備のCVE-2026-54400(CVSS 9.1)の2件が確認された。残るUniFi OS/Protect関連では、SSRF(サーバーサイドリクエストフォージェリ)やCORS設定不備に類する脆弱性としてCVE-2026-54402(CVSS 9.9)とCVE-2026-55115(CVSS 9.9)、そしてアクセス制御不備のCVE-2026-55116(CVSS 9.0)が報告されている(これら2件の技術的な性質については報道により表現に差異がある)。Ubiquitiは各製品について、UniFi Connect 3.4.20、UniFi Talk 5.2.2、UniFi Access 4.2.29、UniFi Protect 7.1.83、UniFi OS 5.1.19以降への更新でこれらの脆弱性に対応している。

## 背景と今後の見通し

Ubiquiti製品を巡っては過去にも深刻なセキュリティ事案が繰り返されてきた。2024年2月にはFBIがロシア関連のボットネット「Moobot」によるUbiquiti Edge OSルーターの悪用を摘発しており、ロシア国家支援の攻撃者がUbiquiti製ルーターをボットネットに組み込んでいたとの報告もある。さらに直近の2026年6月には、米CISAがUniFi OSに関する既知の3件の重大脆弱性を「実際の攻撃で悪用されている」として既知悪用脆弱性(KEV)カタログに追加したばかりだった。このように、UniFi OS関連製品は攻撃者にとって継続的に狙われやすいターゲットとなっている。今回の7件については現時点で実悪用の確認はないものの、コマンドインジェクションやSQLインジェクションといった深刻度の高い脆弱性が短期間に相次いで発見されている状況を踏まえ、UniFi製品を利用する組織や個人は速やかにパッチ適用済みバージョンへアップデートすることが強く推奨される。
