---
date: "2026-04-18T18:14:53+09:00"
title: "13年前から潜在したApache ActiveMQの脆弱性CVE-2026-34197がCISA KEVに追加、連邦機関に4月30日までのパッチ適用を義務付け"
description: "CISAがApache ActiveMQ Classicに存在する13年前からの高深刻度脆弱性CVE-2026-34197をKEVカタログに追加し、実際の攻撃での悪用が確認されたとして連邦機関に4月30日までのパッチ適用を義務付けた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/cisa-flags-apache-activemq-flaw-as-actively-exploited-in-attacks/"
  - "https://www.theregister.com/2026/04/17/cisa_tells_feds_to_patch/"
  - "https://securityaffairs.com/190917/security/u-s-cisa-adds-a-flaw-in-apache-activemq-to-its-known-exploited-vulnerabilities-catalog.html"
---

## 概要

米国サイバーセキュリティ・インフラセキュリティ庁（CISA）は2026年4月16日、Apache ActiveMQ Classicに存在する高深刻度の脆弱性**CVE-2026-34197**（CVSSスコア8.8）を既知の悪用された脆弱性（KEV）カタログに追加した。この脆弱性は13年間にわたって検出されないまま存在し続けており、Horizon3のセキュリティ研究者Naveen Sunkavally氏によって発見されたものだ。Apacheは3月30日にパッチを提供しているが、ShadowServerの調査によると現在も8,000件を超えるActiveMQインスタンスがインターネットに公開されている状態にある。

## 脆弱性の技術的詳細

CVE-2026-34197はApache ActiveMQのJolokia JMX-HTTPブリッジにおける不適切な入力検証の問題に起因する。認証済みの攻撃者がJolokia管理APIを通じた管理操作を悪用し、ブローカーに細工されたURIを送信することでリモートのSpring XML設定ファイルを読み込ませ、任意のOSコマンドを実行できる。Springはバリデーション前にBeanをインスタンス化するため、`Runtime.exec()`などの手法を通じた任意コード実行が可能となる。

この脆弱性は表面上は認証が必要だが、実際の悪用は現実的だ。多くのデプロイメントでデフォルト認証情報（`admin:admin`）が使われたままになっていることに加え、バージョン6.0.0〜6.1.1に存在するCVE-2024-32114を組み合わせると、Jolokiaへの認証なしのアクセスが可能となり、未認証のリモートコード実行チェーンが構成される。影響を受けるバージョンはActiveMQ Classic 5.19.4未満および6.2.3未満であり、修正済みバージョン（5.19.4または6.2.3以降）へのアップグレードが推奨される。攻撃の痕跡調査には、ブローカーログ内の`brokerConfig=xbean:http://`パラメータやVMトランスポートプロトコルを使った不審な接続の確認が有効とされている。

## CISAの対応と影響範囲

CISAはBOD 22-01（Binding Operational Directive）に基づき、連邦民間行政機関（FCEB）に対して2026年4月30日までにすべてのシステムへのパッチ適用を義務付けた。なお、CISAが実際に悪用されたとして報告したApache ActiveMQの脆弱性はこれで3件目となる。

組織はただちにパッチ済みバージョンへのアップグレードを優先し、インターネットへの不必要な公開を避けるようアクセス制限を見直すことが求められる。

