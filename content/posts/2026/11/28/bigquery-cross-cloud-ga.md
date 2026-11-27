---
date: "2026-11-28T08:07:20+09:00"
title: "BigQueryの「クロスクラウド接続」が正式GA、AWS・Azure・Salesforce Data 360を全リージョンから直接クエリ可能に"
description: "Google CloudがBigQueryのクロスクラウド接続機能を正式リリースし、BigQuery Omniを介さずAWSやAzure、Salesforce Data 360上のデータを全リージョンから直接クエリできるようになった。"
tags:
  - Cloud
references:
  - "https://docs.cloud.google.com/bigquery/docs/release-notes"
---

## 概要

Google Cloudは11月25日、BigQueryの「クロスクラウド接続(cross-cloud connections)」機能を正式リリース(GA)したと発表した。この機能により、AWSやAzure、Salesforce Data 360上に存在するデータを、BigQuery Omniを使わずにBigQueryの全リージョンから直接クエリできるようになる。これまでマルチクラウド環境でのデータ分析にはBigQuery Omniを経由する必要があったが、クロスクラウド接続はより多くの機能を利用できる点が特徴として挙げられている。

## BigQuery Omniとの違いと経緯

BigQuery Omniは、AWSやAzure上のデータをBigQueryのインターフェースから分析できるようにするサービスとして提供されてきたが、利用にあたってはOmniが対応する特定のリージョンでBigQueryを実行する必要があるなど、構成上の制約があった。今回GAとなったクロスクラウド接続は、こうした制約を緩和し、BigQueryを実行しているリージョンを問わず、AWS・Azure・Salesforce Data 360上のデータへ直接アクセスできる点が最大の違いとなる。この機能は2026年8月3日にプレビューとして発表されており、約4ヶ月の検証期間を経て今回GAに至った。

## 今後の展望

マルチクラウド構成を採用する企業にとって、データ基盤をどこに置くかはコストやガバナンス上の大きな課題となってきた。クロスクラウド接続のGA化により、企業は既存のAWSやAzure、Salesforce Data 360上のデータをそのままの場所に置きつつ、BigQueryの分析機能やリージョン選択の自由度を損なわずに利用できるようになる。BigQuery Omniからの移行や使い分けの指針については、今後Google Cloudから追加のガイダンスが示されることが期待される。
