---
date: "2026-10-02T18:14:45+09:00"
title: "Cisco SD-WAN ManagerにURIエンコードを悪用した認証バイパスの実攻撃、CISAがKEVに追加し連邦機関に10月3日までの対応を命令"
description: "Cisco Catalyst SD-WAN Managerの認証バイパス脆弱性CVE-2026-76504(CVSS 9.8)が実際の攻撃で悪用され、CISAがKEVカタログに追加して連邦機関に緊急対応を命じた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/cisco-warns-of-new-sd-wan-authentication-bypass-zero-day-exploited-in-attacks/"
  - "https://thehackernews.com/2026/09/cisco-warns-of-attackers-exploiting.html"
  - "https://thehackernews.com/2026/10/cisa-adds-exploited-cisco-catalyst-sd.html"
---

## 概要

Ciscoは、Catalyst SD-WAN Managerに存在する深刻な認証バイパスの脆弱性(CVE-2026-76504、CVSS スコア9.8)が実際の攻撃で悪用されていると警告した。この脆弱性を突かれると、無認証の遠隔攻撃者がログイン情報を一切持たないまま管理APIにアクセスし、デフォルトでnetadminロール(デバイスに対するあらゆる操作が可能な権限)を持つadminユーザーとして振る舞えるようになる。設定内容にかかわらず、すべてのCatalyst SD-WAN Manager環境が影響を受ける。CiscoのPSIRT(製品セキュリティインシデント対応チーム)は、2026年9月にテクニカルサポート対応の過程で実際の悪用を確認したとしているが、攻撃件数や攻撃者の身元については明らかにしていない。

## 技術的な詳細

脆弱性の原因は、HTTPリクエスト中のURIエンコーディングの処理不備にある。セッションベースのログインに使われる`j_security_check`エンドポイントを保護する認証ルールに対し、攻撃者は"j"を表す"%6a"のような文字エンコーディングを用いた細工済みリクエストを送ることで、認証チェックをすり抜けてしまう。攻撃者に必要なのは、公開されたManagerインスタンスへHTTPリクエストを送信できることだけであり、インターネットに露出した環境は即座に侵害のリスクにさらされる。

影響を受けるのは20.9系、20.12系、20.15系、20.18系、26.1系、26.2系で、それぞれ20.9.10.1、20.12.8.2、20.15.6.1、20.18.4.1、26.1.2.1、26.2.1への更新で修正される。Ciscoは、管理インターフェース(ポート443、22、830)へのインターネットアクセスを制限するよう推奨するとともに、`/var/log/nms/containers/service-proxy/serviceproxy-access.log`や`vmanage-server.log`を調査し、見慣れないIPアドレスからの`j_security_check`関連のアクセスや、"viptela-reserved-"で始まるユーザー名のエントリがないか確認するよう呼びかけている。

## CISAの対応と背景

CISAは本脆弱性を既知の悪用済み脆弱性(KEV)カタログに追加し、「URIエンコーディングの不適切な処理により、無認証の遠隔攻撃者がadminユーザーの権限で対象システムにアクセスできる」と説明した。これを受けて連邦民間行政機関(FCEB)には、10月3日までに修正を適用することが義務付けられている。

SD-WAN Managerを狙った攻撃はこれが初めてではなく、報道によれば年初来5件目のSD-WANゼロデイ脆弱性の実悪用例とされ、2026年だけで8件のCisco SD-WAN関連CVEがKEVカタログに追加されている。ネットワーク全体の制御を担うSD-WAN基盤が攻撃者にとって価値の高い標的になっていることがうかがえる。企業のネットワーク管理者には、パッチ適用とあわせてログの精査、管理インターフェースの外部露出の遮断など、早急な対応が求められる。
