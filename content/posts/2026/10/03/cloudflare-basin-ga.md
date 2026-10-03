---
date: "2026-10-03T18:12:55+09:00"
title: "Cloudflareがサーバーレスデータ分析基盤「Basin」を正式提供、PipelinesとCatalog、SQLを統合しエグレス無料を強調"
description: "CloudflareがApache IcebergとR2を基盤とするサーバーレスデータ分析プラットフォーム「Basin」を正式リリースし、専用インフラ不要・エグレス料金なしでの分析を可能にした。"
tags:
  - Cloud
references:
  - "https://blog.cloudflare.com/cloudflare-basin/"
  - "https://siliconangle.com/2026/10/01/cloudflare-moves-into-analytics-workloads-with-a-serverless-alternative-that-doesnt-require-dedicated-servers-or-data-movement/"
  - "https://www.theregister.com/databases/2026/10/01/cloudflare-launches-data-platform-with-bland-basin-branding-promise-of-fewer-fees/5300618"
---

## 概要

Cloudflareは10月1日、Birthday Weekのタイミングでサーバーレスデータ分析プラットフォーム「Basin」を正式にリリースした。Apache IcebergとR2オブジェクトストレージ上に構築されており、専用サーバーの用意やデータ移動を必要とせずにデータの取り込みから分析までを一貫して行える。最大の特徴はエグレス料金が発生しない点で、利用量に応じた課金のみで済むため、専用のデータ基盤を構築するには規模が小さすぎた中小企業や開発者チームでも手頃に分析環境を導入できるとしている。CTOのDane Knechtは「開発者は自分たちのデータを照会するためだけにデータインフラの運用方法を知る必要はないはずだ」と述べており、運用の簡素化を前面に押し出した製品であることがうかがえる。

## 3つのコンポーネントへの統合

Basinはベータ版だった「Cloudflare Data Platform」からのリブランドで、これまで別々に提供されていた3つのプロダクトを統合した。データ取り込みを担う「Basin Pipelines」（旧Cloudflare Pipelines）はWorkers、HTTPエンドポイント、Cloudflare LogpushからのイベントをSQLで変換し、Apache IcebergテーブルやR2上のJSON/Parquetファイルに出力する機能を持ち、1ストリームあたり最大3GB/秒の取り込みに対応する。カタログ管理を担う「Basin Catalog」（旧R2 Data Catalog)はフルマネージドのApache Iceberg REST カタログで、テーブルごとのコンパクション、スナップショットの失効処理、マニフェスト最適化などのメンテナンスを自動で行い、`npx wrangler basin catalog create`のワンコマンドで作成できる。クエリエンジンの「Basin SQL」（旧R2 SQL）はIcebergテーブル向けのサーバーレス分散クエリエンジンで、190以上の関数やJOIN、ウィンドウ関数、CTE、グルーピングセットなど複雑なクエリに対応する。既存のPipelines、R2 Data Catalog、R2 SQLの設定はそのまま動作するため、移行の負担は小さい。

## オープン標準とエコシステムとの連携

BasinはApache Icebergというオープンな標準フォーマットを採用しているため、PyIceberg、DuckDB、Snowflake、Apache Spark、StarRocks、Trinoといった既存のIceberg対応エンジンからそのままデータを参照できる。これによりベンダーロックインを避けつつ、複数のクラウドやエンジンをまたいでデータを再コピー・再フォーマットせずに分析できる点が強みとなる。実際にBasinへ移行した企業の例として、Anomaly共同創業者のDax Raadは「複雑なAWS S3とAthenaの構成を、よりシンプルなサーバーレス構成であるBasin Pipelines、Catalog、SQLに置き換えて、全社のデータパイプラインを移行した」と述べている。想定される用途としては、リアルタイムのEコマース最適化、長期的な課金メトリクスの保存・レポーティング、インフラのテレメトリ収集・照会、AIで利用しやすい形でのデータ配信プラットフォームなどが挙げられている。

## 料金面の注意点と競合における位置づけ

Cloudflareは「エグレス料金なし」を強調しているが、The Registerの指摘によれば無料となるのはWorkers API・S3 API・パブリックドメイン経由のR2からの直接エグレスや、クロスプラットフォーム・クロスリージョンでのクエリに限られる。Basin Pipelinesが「シンク」と呼ばれる配信先にデータを送信する際には、無料枠を超えると別途課金が発生し、R2バケットに接続する外部サードパーティサービス側で課金が生じる可能性もある。Constellation ResearchのMichael Niは、Basinについて「Cloudflareは従来型データウェアハウス市場の周縁にあるワークロードを取り込み、そこから上位層へ展開していく機会を得ている」と分析しており、SnowflakeやDatabricksといった既存プレイヤーとの直接競合ではなく、これまで手薄だった中小規模の分析ニーズを取り込む狙いがあるとみられる。CDNやセキュリティ事業で知られるCloudflareが、エッジネイティブなデータ分析市場へ本格的に踏み出した動きとして注目される。
