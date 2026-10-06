---
date: "2026-10-06T18:15:12+09:00"
title: "Exchange Serverに他ユーザーのメールを閲覧できる脆弱性、Microsoftが緊急パッチを公開"
description: "MicrosoftはオンプレミスExchange Serverの権限昇格の脆弱性CVE-2026-96940(CVSS 8.8)を修正する帯域外更新を公開したが、カレンダー表示エラーなどの副作用も報告されている。"
tags:
  - Security
references:
  - "https://www.helpnetsecurity.com/2026/10/05/exchange-server-vulnerability-cve-2026-96940/"
  - "https://thehackernews.com/2026/10/microsoft-exchange-flaw-lets.html"
  - "https://www.heise.de/en/news/Microsoft-pushes-Exchange-update-11475574.html"
---

## 概要

Microsoftは10月5日、オンプレミス版Exchange Serverに存在する権限昇格の脆弱性CVE-2026-96940(CVSSスコア8.8、「高」深刻度)を修正する帯域外(Out-of-band)更新プログラムを公開した。この脆弱性は「Weak authorization in Microsoft Exchange Server allows an authenticated attacker to elevate privileges over a network」と説明されており、認証済みの攻撃者が同一組織内の他ユーザーのメールボックスへ不正にアクセスし、メール本文や添付ファイルを読み取れてしまう。ただしテナント境界は維持されており、組織の外へアクセスが及ぶことはない。脆弱性はMicrosoftのセキュリティ研究者Jan Mitchellによって発見され、Microsoftは「悪用される可能性が高い(Exploitation More Likely)」と評価する一方、現時点で野生での悪用報告は確認されていないとしている。

## 影響を受けるバージョンと対応

今回の脆弱性は、Exchange Server Subscription Edition RTM、Exchange Server 2019(累積更新14および15)、Exchange Server 2016(累積更新23)が対象となる。サポートが切れた古いバージョンについては、Extended Security Update(ESU)プログラムのPhase 2契約が必要になる。クラウド側のExchange Onlineは既にサービス側の対応が完了しており、ハイブリッド構成のクラウドサーバーについても自動的にパッチが適用済みだが、オンプレミス環境の管理者は手動で更新プログラムを適用する必要がある。なお、Microsoftは先週Exchange Online向けの修正を展開した際に説明資料(KB記事)を伴わずに公開して利用者を驚かせたが、後にこのリリース順序が意図したスケジュールより早まった異例のものだったと説明する一幕もあった。

## 副作用と今後の対応

今回の更新プログラムには複数の副作用が報告されている。カレンダーを公開している環境ではHTTP 500エラーが返される場合があり、また韓国語の単語分割ルールの欠落によりContentEngineがデッドロックを起こす不具合も確認されている。Microsoftはこれらについて今後の更新で修正する予定としている。一方で、今回のパッチは共有メールボックスの委任設定やハイブリッド環境におけるGraph APIの予定情報取得に関する問題も合わせて解消している。権限昇格による情報漏洩のリスクが高いと評価されていることから、オンプレミスでExchange Serverを運用する組織には早期の適用が推奨される。
