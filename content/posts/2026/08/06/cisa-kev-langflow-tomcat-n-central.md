---
date: "2026-08-06T08:19:34+09:00"
title: "CISA、Langflow・Apache Tomcat・N-central の実悪用中の脆弱性3件をKEVカタログに追加"
description: "CISAがLangflow(CVSS 9.8)、Apache Tomcat、N-able N-centralの実悪用中の脆弱性3件をKEVカタログに追加し、連邦機関に8月7日までのパッチ適用を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/08/cisa-flags-langflow-rce-tomcat-and-n.html"
  - "https://www.bleepingcomputer.com/news/security/cisa-warns-of-hackers-exploiting-langflow-n-central-apache-tomcat-flaws/"
  - "https://www.securityweek.com/cisa-warns-of-exploited-langflow-n-central-and-tomcat-vulnerabilities/"
---

## 概要

米サイバーセキュリティ・インフラセキュリティ庁(CISA)は2026年8月5日、実際に悪用が確認されている3件の脆弱性を「既知の悪用脆弱性(KEV)」カタログに新たに追加した。対象はIBMのLangflow、Apache Tomcat、N-ableのN-centralで、連邦民間行政機関(FCEB)に対しては拘束的運用指令(BOD 26-04)に基づき、8月7日(金)までのパッチ適用が義務付けられている。

## 脆弱性の詳細

最も深刻なのはLangflow(OSS版AIワークフロー構築ツール)のリモートコード実行脆弱性(CVE-2026-9198)で、CVSSスコアは最大値に近い9.8。認証なしの攻撃者が2つのAPIエンドポイントを連鎖させることでログイン認証をバイパスしてスーパーユーザートークンを取得し、任意のPythonコードを実行できる。デフォルト構成のすべての展開が影響を受け、開発元は7月17日にバージョン1.10.1でパッチを提供したが、7月24日頃には完全な概念実証(PoC)コードが公開されていた。

Apache Tomcatの脆弱性(CVE-2026-34486、CVSS 7.5)は、クラスタノード間通信を暗号化するEncryptInterceptorをバイパスできるというもの。実はこれ自体が、3月に修正されたクリティカル脆弱性CVE-2026-29146(CVSS 9.8)への対応時に、1行のコードを移動したことで暗号化層が「フェイルオープン」状態になってしまったことが原因とされる。修正版はバージョン11.0.21、10.1.54、9.0.117で4月に提供済み。7月30日にはPalo Alto Networksが、中国語圏の脅威アクターがこの欠陥を突いて9台のTomcatサーバーにリバースシェルを仕掛けたと報告しており、攻撃グループ「knaithe」や「KnYuan」がAIエージェント基盤「Hermes」を使って攻撃を自動化していたとされる。

N-able N-centralのリモート監視管理(RMM)プラットフォームでは、認証バイパスによってゼロデイ攻撃で管理者アカウントが乗っ取られる脆弱性(CVE-2026-18556、CVSS 7.4程度)が確認された。当初のパッチが不完全だったため、攻撃者は新たなバイパス手法(CVE-2026-18577)を発見し、N-ableは8月1日に悪用の注意喚起を行った上で緊急ホットフィックスをリリースしている。

## 攻撃活動の広がり

各社の報道によれば、これらの脆弱性を悪用した攻撃はAIを活用した自動ハッキングキャンペーンの一環として展開されており、自律的な攻撃技術と手動の侵入テクニックを組み合わせた手法で460以上の標的が狙われたとされる。Tomcatの脆弱性はLinux向けドロッパーマルウェア「SNOWLIGHT」の配布にも利用されており、単発の攻撃ではなく組織的なキャンペーンの一部であることがうかがえる。

## 今後の対応

CISAの命令は連邦機関を対象としたものだが、いずれの脆弱性もすでに実悪用が確認され、PoCも公開されていることから、Langflow、Tomcat、N-centralを利用する民間組織にとっても緊急のパッチ適用が強く推奨される。特にN-centralのような不完全な初期パッチが再び回避されたケースは、パッチ適用後も継続的な監視が必要であることを改めて示している。
