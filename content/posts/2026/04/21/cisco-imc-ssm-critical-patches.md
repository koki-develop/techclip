---
date: "2026-04-21T02:29:40+09:00"
title: "CiscoがIMCとSSM On-PremのCVSS 9.8の重大脆弱性を修正、認証バイパスとroot権限奪取のリスク"
description: "CiscoはIntegrated Management Controller（IMC）とSmart Software Manager On-Prem（SSM On-Prem）に存在するCVSSスコア9.8の重大な脆弱性2件を修正するパッチをリリースした。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/cisco-patches-98-cvss-imc-and-ssm-flaws.html"
  - "https://www.bleepingcomputer.com/news/security/critical-cisco-imc-auth-bypass-gives-attackers-admin-access/"
  - "https://www.greenbone.net/en/blog/patch-now-critical-severity-flaws-in-cisco-ssm-on-prem-and-imc-plus-more/"
---

## 概要

Ciscoは2026年4月、エンタープライズインフラ管理システムに関わる重大な脆弱性2件（CVE-2026-20093、CVE-2026-20160）に対するセキュリティパッチをリリースした。いずれもCVSSスコアは9.8（Critical）であり、認証を一切必要とせずリモートから悪用可能なため、影響を受ける組織は直ちにパッチを適用する必要がある。現時点では野生での悪用やPublic PoC（概念実証コード）は確認されていないが、過去に同社製品の脆弱性がランサムウェアグループに利用された経緯があり、迅速な対応が求められる。

## 脆弱性の詳細

**CVE-2026-20093（Cisco IMC）**は、Integrated Management Controller（IMC/CIMC）のパスワード変更処理の不備に起因する認証バイパスの脆弱性だ。攻撃者は細工したHTTPリクエストを送信するだけで、認証なしにシステム上のすべてのユーザー（管理者を含む）のパスワードを変更し、完全な管理者権限を取得できる。IMCはCisco UCS C-SeriesおよびE-Seriesサーバーのマザーボードに組み込まれたアウトオブバンド管理モジュールであり、XML API・WebUI・CLIを通じてアクセスされる。エンタープライズのコアワークロードに隣接して動作することが多いため、侵害された場合はネットワーク内の横断移動（ラテラルムーブメント）の起点となり得る。

影響を受ける製品と修正済みバージョンは以下のとおり：
- UCS C-Series M5/M6（スタンドアロン）: 4.3(2.260007)、4.3(6.260017)、6.0(1.250174)
- Catalyst 8300 Edge uCPE: 4.18.3
- ENCS 5000 Series: 4.15.5
- UCS E-Series M3: 3.2.17
- UCS E-Series M6: 4.15.3

**CVE-2026-20160（Cisco SSM On-Prem）**は、Smart Software Manager On-Premの内部サービスAPIが外部に露出していることに起因する未認証リモートコード実行の脆弱性だ。攻撃者は細工したAPIリクエストを送信することで、基盤となるOSでroot権限の任意コマンドを実行できる。修正済みバージョンはSSM On-Prem 9-202601。

## 対応と推奨事項

両脆弱性ともワークアラウンド（回避策）は存在しないため、Ciscoは提供済みパッチへの即時アップグレードを強く推奨している。組織はまずSSM On-PremおよびIMCインスタンスのネットワーク露出状況を確認し、インターネットや不要なネットワークセグメントからアクセスできないよう、ネットワークセグメンテーションと最小権限の原則に基づくアクセス制御を実施することが重要だ。Greenboneの「OpenVAS Enterprise Feed」ではこれらの脆弱性を検出するためのチェックがすでに提供されており、脆弱性スキャナーを活用した環境の継続的な監視も有効な対策となる。