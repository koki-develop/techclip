# AWS、Aurora PostgreSQLにDuckDBを統合、ETLなしでデータレイクを直接クエリ可能に
Tags: Cloud

- AWS、Aurora PostgreSQLにDuckDBを統合しETL不要でデータレイクを直接クエリ可能に (2026-10-08)
  https://www.publickey1.jp/blog/26/awsduckdbaurora_postgresqletl.html
- AWS Launches Aurora Capability to Query Data Lakes Without Moving the Data (2026-10-02)
  https://www.hpcwire.com/bigdatawire/2026/10/02/aws-launches-aurora-capability-to-query-data-lakes-without-moving-the-data/
- AWS Embeds DuckDB in Aurora to Collapse Operational and Lakehouse Silos (2026-10-07)
  https://futurumgroup.com/insights/aws-embeds-duckdb-in-aurora-to-collapse-operational-and-lakehouse-silos/

AWSがAurora PostgreSQLに分析エンジンDuckDBを組み込み、Apache IcebergやParquet形式で保存されたS3上のデータレイクを、ETL処理やデータ移動なしに通常の運用データと同一のSQLクエリで横断的に扱えるようにした。オペレーショナルDBと分析基盤に分かれていたデータ活用の壁を取り払い、リアルタイム分析のコストと複雑さを削減する狙いがある。
