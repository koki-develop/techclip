---
date: "2026-10-09T18:17:51+09:00"
title: "AWS、Aurora PostgreSQLにDuckDBを統合、運用データとデータレイクをETLなしで統一クエリ"
description: "AWSはAurora PostgreSQLにDuckDBのベクトル化クエリエンジンを組み込み、S3上のIcebergやParquet形式のデータレイクをETLなしで運用データと統一的にクエリできるようにした。"
tags:
  - Cloud
references:
  - "https://www.publickey1.jp/blog/26/awsduckdbaurora_postgresqletl.html"
  - "https://www.hpcwire.com/bigdatawire/2026/10/02/aws-launches-aurora-capability-to-query-data-lakes-without-moving-the-data/"
  - "https://futurumgroup.com/insights/aws-embeds-duckdb-in-aurora-to-collapse-operational-and-lakehouse-silos/"
---

## 概要

AWSは2026年9月30日、Amazon Aurora PostgreSQLにDuckDBを組み込んだことを発表した。これにより、Aurora上の運用データとApache IcebergやParquet形式でAmazon S3に保存されたデータレイクを、ETL処理やデータ移動なしに単一のSQLクエリで横断的に扱えるようになった。従来、運用データベースと分析基盤(データレイク/レイクハウス)は別々のシステムとして運用され、両者をつなぐにはリバースETLパイプラインを構築・維持する必要があった。この統合はその運用負担を取り除き、リアルタイム分析のコストと複雑さを削減することを狙う。

## 技術的な仕組み

背景には、AWSが2026年9月にDuckDBの開発元であるDuckLabsを買収したことがある。AWSはこれによりDuckDBのベクトル化(列指向)クエリエンジンを、Aurora PostgreSQL 17/18のコアに拡張機能および外部データラッパーとして直接組み込んだ。DuckDBはもともと「SQLiteのようにアプリケーションに組み込める小型で高速なOLAP処理エンジン」であり、並列実行可能な列指向エンジンを備える。データレイク側はApache IcebergおよびParquet形式(CSV、JSONにも対応)に対応し、AWS Glue Data CatalogやIceberg REST Catalogを経由してS3およびS3 Tables上のデータにアクセスする。スキーマの自動推論、述語プッシュダウン、列プルーニングといった最適化により、S3への不要なリクエストを抑えつつ、本番データベースのライブデータとS3上の履歴データを同一クエリ内で同時に処理できる。

## 狙いと今後の展望

この仕組みにより、データのコピーや変換、同期の遅延といったETL特有の手間が解消される。特にAIエージェント開発においては、同一セッション内で履歴データの検査とトランザクションの書き込みを即座に行えるようになる点が評価されている。アナリストのBrad Shimmin氏は、この統合が「リバースETLパイプラインの運用負担を除去する」ものであり、AIエージェントにとって「履歴データ検査と即座のトランザクション書き込みを同一セッションで実現する」と指摘する。一方で、メモリ消費量の実測、IcebergテーブルへのACID準拠の書き込み機能の拡張、外部Iceberg REST Catalogの採用動向など、実運用に向けて注視すべき点も残されている。DuckLabsは買収後もDuckDB本体のオープンソース開発(MITライセンス)を継続する方針であり、オペレーショナルDBと分析基盤の境界を取り払う動きは今後も広がっていく可能性がある。
