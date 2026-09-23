---
date: "2026-09-24T08:09:47+09:00"
title: "F5 BIG-IP APMにCVSS9.8のゼロデイ、OAuth認可サーバー構成で認証不要のRCEが実悪用"
description: "F5がBIG-IP Access Policy ManagerのOAuth認可サーバー構成に存在するCVSS9.8のゼロデイ脆弱性CVE-2026-94127を修正し、CISAが連邦機関に9月25日までの緊急対応を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/f5-patches-critical-big-ip-apm-zero-day.html"
  - "https://www.bleepingcomputer.com/news/security/f5-warns-of-big-ip-apm-remote-code-execution-zero-day-exploited-in-attacks/"
  - "https://www.securityweek.com/critical-f5-big-ip-vulnerability-exploited-as-zero-day/"
---

## 概要

F5は、BIG-IP Access Policy Manager(APM)に存在するヒープベースのバッファオーバーフロー脆弱性CVE-2026-94127を修正した。CVSSスコアはv3.1で9.8、v4.0で9.3と極めて深刻度が高く、認証なしでリモートコード実行(RCE)が可能となる。F5はこの脆弱性が既に実際の攻撃で悪用されていることを確認しており、CISAは同日、既知悪用脆弱性(KEV)カタログに追加した上で、連邦政府機関に対し9月25日までの緊急パッチ適用ないし軽減策の適用を義務付けた。

## 脆弱性の詳細と影響範囲

脆弱性が影響するのは、BIG-IP APMが「OAuth認可サーバー」として構成されているケースに限定される。具体的には、APMのアクセスポリシーとOAuth認可サーバープロファイルが同一の仮想サーバー上に構成されている場合が対象で、APMをOAuthクライアントやリソースサーバーとしてのみ利用している構成は影響を受けない。該当条件を満たす仮想サーバーに悪意のあるトラフィックを直接送信することで、認証を経ずにリモートコード実行が可能になる点が特に危険視されており、BIG-IPの管理インターフェースへのアクセスを制限するだけでは防御にならない。影響を受けるバージョンは21.1.0、17.5.0~17.5.1、17.1.0~17.1.3で、Applianceモードで運用している場合も対象となる。F5はブランチごとにホットフィックス(Hotfix-BIGIP-21.1.0.2.0.30.22-ENG、Hotfix-BIGIP-17.5.1.9.0.160.12-ENG、Hotfix-BIGIP-17.1.3.5.0.41.14-ENG)を提供している。

## 実悪用の兆候と検知方法

F5は攻撃の痕跡として、APMログ内での複数のOAuth認証失敗(UserInfoリクエストの失敗を含む)や、OAuthカウンターのtotal_failed値の不可解な上昇、監査ログにおける疑わしいコマンド実行、そしてこれらに続くTMM(Traffic Management Microkernel)のコアファイル生成やSIGABRTシグナルの発生を挙げている。セキュリティ企業Shadowserverの観測では、インターネット上にBIG-IP APMのフィンガープリントを持つIPアドレスが14,700件以上存在するとされるが、この数値にはパッチ適用済みのシステムやハニーポットも含まれ得るため、実際に脆弱な状態にあるシステム数を正確に示すものではない。

## 対応状況と背景

CISAは2026年9月22日付でCVE-2026-94127をKEVカタログに登録し、BOD 26-04に基づき連邦機関に9月25日までの対応を命じた。即座にパッチを適用できない組織に対しては、F5サポートを通じて提供される一時的なiRuleベースの軽減策を先に適用し、その後ベンダーパッチを導入するよう推奨している。今回の一件は、F5にとって2021年11月以降8件目となる実悪用済み脆弱性であり、2025年8月にはBIG-IPの未公開ソースコードが攻撃者に窃取される侵害も発生している。同社製品を狙った攻撃が継続的に確認されている状況を踏まえ、該当バージョンを利用する組織は速やかな対応が求められる。
