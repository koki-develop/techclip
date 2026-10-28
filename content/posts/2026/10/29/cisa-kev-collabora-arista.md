---
date: "2026-10-29T08:08:19+09:00"
title: "CISA、Collabora OnlineとArista VeloCloudの重大脆弱性2件を既知の悪用カタログに追加"
description: "米CISAがCollabora Online(CODE Server)のコマンドインジェクションとArista VeloCloud OrchestratorのSQLインジェクションを既知の悪用脆弱性カタログに追加し、連邦機関に修正適用を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/10/cisa-flags-two-actively-exploited.html"
---

## 概要

米CISA(サイバーセキュリティ・インフラセキュリティ庁)は、Nextcloud上で動作するCollabora Online(組み込みCODE Server)とArista VeloCloud Orchestratorに存在する重大な脆弱性2件を、既知の悪用脆弱性(KEV)カタログに追加した。両脆弱性はいずれもCVSSスコアが9点台と評価される深刻なもので、実際の攻撃で悪用が確認されている。連邦機関に対しては2026年10月26日までの修正適用が義務付けられた。

## Collabora Onlineの脆弱性(CVE-2026-110447)

CVE-2026-110447はCVSSスコア9.2のOSコマンドインジェクションの脆弱性で、Collabora Online Built-in CODE ServerをNextcloud上で利用している環境が対象となる。"proxy.php"を経由し、CODEのローカルドキュメントサーバーが稼働していない状態でリモートコード実行を許す点が特徴だ。修正は2026年9月公開のバージョン26.4.303で行われている。攻撃者はこの脆弱性を悪用してNextcloudサーバーにWebシェルをバックドアとして設置し、認証情報ストア、パスワードマネージャーの成果物、暗号資産ウォレットを探索する偵察活動を行っていたことが確認されている。

## Arista VeloCloudの脆弱性(CVE-2026-114625)

もう一方のCVE-2026-114625は、オンプレミス版Arista VeloCloud Orchestrator(VCO)に存在するSQLインジェクションの脆弱性で、CVSSスコアは9.9とさらに深刻だ。悪用にはVCOのWebインターフェースへのネットワークアクセスと有効な認証セッションが必要となるが、必要な権限は「Enterprise Read Only」という最小限のユーザーロールで足りる。修正パッチはバージョン5.2.3.18、6.1.3.10、6.4.2.12で2026年10月に公開された。Aristaは脆弱性が積極的に悪用されていることを認めているものの、攻撃者の具体的な帰属や侵入後の行動については詳細を開示していない。攻撃元として日本に位置する2つのIPアドレス(74.82.197[.]86、38.54.50[.]151)が観測されている点も報告されている。なお、VCOに関しては今回の脆弱性が7月以降に悪用が確認された3件目であり、先行する2件はいずれもCVSSスコア10.0の最高レベルだったという経緯がある。

## 今後の対応

両脆弱性とも修正パッチが既に公開されているため、Nextcloud/Collabora OnlineおよびArista VeloCloud Orchestratorの運用者は速やかなバージョン更新が求められる。特にVeloCloudは短期間に複数の重大脆弱性が相次いで悪用されている実態があり、ネットワーク境界を管理するSD-WANオーケストレーターという製品特性上、侵害された場合の影響範囲が大きい点にも注意が必要だ。KEVカタログへの登録は連邦機関への対応義務を伴うが、民間企業においても優先度の高いパッチ適用対象として扱うべき事案といえる。
