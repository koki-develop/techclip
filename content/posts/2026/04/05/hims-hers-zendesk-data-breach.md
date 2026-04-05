---
date: "2026-04-05T10:37:07+09:00"
title: "Hims & HersがZendesk経由のデータ侵害を公表、ShinyHuntersによるOkta SSO悪用攻撃の一環"
description: "テレヘルス大手Hims & Hers Healthが、ShinyHuntersグループによるZendesk上のサポートチケットへの不正アクセスを公表し、顧客の氏名・連絡先情報が漏洩した可能性があると警告した。"
tags:
  - Security
references:
  - "https://techcrunch.com/2026/04/02/telehealth-giant-hims-hers-says-its-customer-support-system-was-hacked/"
  - "https://www.bleepingcomputer.com/news/security/hims-and-hers-warns-of-data-breach-after-zendesk-support-ticket-breach/"
---

## 概要

米国のテレヘルス大手Hims & Hers Healthは2026年4月、カスタマーサポートプラットフォームのZendeskへの不正アクセスによりデータが漏洩した可能性があると顧客に通知した。侵害は2026年2月4日から7日にかけて発生し、同社は2月5日に検知、3月3日に侵害を確認した後、4月2日に顧客への通知を行った。漏洩した可能性のあるデータはサポートチケットに含まれる氏名・連絡先情報などの個人情報に限定されており、医療記録や医師との通信は侵害されていないと強調している。

## 攻撃手法と攻撃者の帰属

BleepingComputerの報道により、今回の攻撃は悪名高いサイバー恐喝グループ**ShinyHunters**によるものと判明した。攻撃者はOkta SSOアカウントの侵害を足がかりとして、Zendeskのインスタンスへの不正アクセスを実現し、複数の組織から数百万件に及ぶサポートチケットを窃取したとされる。Hims & Hersの被害はこのキャンペーンの一部に過ぎず、同一手法によりManoMano（2026年2月）やCrunchyroll（2026年3月）なども被害を受けており、Zendeskを利用する多数の企業が連続して標的とされていたことが明らかになっている。

## 影響範囲と同社の対応

Hims & Hersは影響を受けた顧客数や漏洩データの全容を公式には開示していないが、被害顧客に対して12か月間の無料クレジットモニタリングを提供するとともに、フィッシング攻撃への警戒強化と信用情報における不審な動きの監視を呼びかけている。今回の事例は、テレヘルス企業が保有する機微な情報を狙った攻撃の深刻さを改めて示しており、サードパーティのSaaSプラットフォームを経由したサプライチェーン型の侵害リスクへの対策が業界全体で急務となっている。
