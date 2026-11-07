---
date: "2026-11-07T18:07:55+09:00"
title: "Google Cloud、Icebergベースのクロスクラウド・レイクハウスをGA化、エグレス料金なしでAWS/Azureのデータに直接クエリ"
description: "Google Cloudが「Agentic Data Cloud」構想を拡張し、エグレス料金なしでAWSやAzure上のデータに直接クエリできるIceberg基盤のクロスクラウド・レイクハウス機能を一般提供し、AlloyDB ExpressやKnowledge Catalogの強化も発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/databases/whats-new-across-googles-agentic-data-cloud"
---

## 概要

Google Cloudは11月4日、AIエージェントが企業内のデータを扱いやすくするための構想「Agentic Data Cloud」の拡張を発表した。中核となるのは、AWSやAzure上に置かれたデータへエグレス料金なしで直接クエリできるApache Icebergベースのクロスクラウド・レイクハウス機能「Borderless Lakehouse」の一般提供（GA）だ。クラウド間をプライベートな相互接続でつなぎ、リモートクラウドのデータブロックをGoogle Cloud側に自動キャッシュする仕組みにより、変動エグレス費用をゼロにしながらクエリを高速化する。Delivery Heroの事例ではデータ移動コストを40%削減したという。あわせて、Databricks Unity・Snowflake Horizon・AWS GlueのIcebergカタログをフェデレーションする機能や、SAP・Workday・SalesforceとのZero-Copy統合、GeminiとのネイティブなIceberg連携も発表されており、企業が複数クラウドに分散したデータをサイロ化せずに一つのレイクハウスとして扱えるようにする狙いがある。

## AlloyDBの新版とデータベース強化

データベース面では、ETLなしでIcebergテーブルを直接クエリできる「AlloyDBとLakehouseの統合」機能が加わり、Amazon互換サービス比で集計クエリが7倍高速化したとしている。また、プレビュー版として2秒以内にプロビジョニングでき、スケール・ツー・ゼロに対応した軽量なPostgres互換サービス「AlloyDB Express」も発表された。1〜2 vCPUと20GBストレージの構成で、コーディングエージェントによる高速な開発・検証用途を想定している。さらに、サブミリ秒のI/Oとテラビット秒級のスキャンスループットを持ち、推論セッション数に応じて自動スケールする「エージェント向けAlloyDB」もプレビューで提供され、本番ワークロードへの影響を抑えながら大量のエージェントアクセスを処理できるとしている。

## Knowledge Catalogの強化とBigQueryの改善

メタデータを統合管理する「Knowledge Catalog」も強化され、Google Workspace・GitHub・Jira・Confluence・SharePointなどの情報源からエージェントのやり取りを基にコンテキストを自動的に進化させる「Self-Learning Enrichment」がプレビューで追加された。社内ベンチマークでは精度が約4倍向上し、レイテンシは33%、トークン消費は75%それぞれ削減されたという。BigQuery・Looker・Databricks・Snowflake・dbt・SAPを横断する「信頼できるセマンティックモデル」もGAとなり、部門が異なっても同じ指標定義を適用できるようにする。あわせてBigQuery自体もFluid scalingなどの最適化によりクエリ速度が40%向上、処理コストは50%削減されたとしており、ペタバイト規模のグラフ分析をETLなしで実行できる「BigQuery Graph」もGAとなった。

## 背景と今後の展望

Google Cloudは、企業がすでに「エージェンティックな時代」に入り、本番環境で稼働するエージェントから価値を得つつある一方で、データが複数クラウドやSaaSに散在していることが精度やコストの課題になっていると説明している。PayPal、Siemens、Telus、Vodafone、Walmartなどの企業が既にAgentic Data Cloudを採用しているとしており、今後は、すでに一般提供されているSpanner Omniのハイブリッド・マルチクラウド対応や、同様に一般提供されたMCPツール経由でのIDE・CLI統合（Data Agent Kit）に加え、数百万規模のエージェントが協調動作する環境への対応を進めているとしている。
