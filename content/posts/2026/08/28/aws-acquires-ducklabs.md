---
date: "2026-08-28T21:53:52+09:00"
title: "AWS、DuckDB開発元DuckLabsを買収 OSSライセンスと財団統治は維持"
description: "AWSが組み込み型分析データベースDuckDBの開発元DuckLabsを買収し、MITライセンスと独立財団による統治を維持しつつS3・Redshiftなどのアナリティクス基盤との統合を強化する。"
tags:
  - Cloud
  - OSS
references:
  - "https://aws.amazon.com/blogs/big-data/aws-and-ducklabs-building-the-future-of-analytics-together/"
  - "https://www.theregister.com/databases/2026/08/26/aws-buys-ducklabs-the-people-behind-the-popular-in-process-olap-database/5292590"
  - "https://siliconangle.com/2026/08/26/aws-buys-ducklabs-to-bring-duckdbs-embeddable-analytics-to-more-enterprises/"
---

## 概要

AWSは、組み込み型のオープンソース分析データベースDuckDBを開発するオランダ・アムステルダム拠点のDuckLabs B.V.を買収することで最終契約を締結したと発表した。買収額は非公開だが、取引は2026年9月の完了を見込んでいる。DuckDBは1日あたり300万件を超えるダウンロードを記録する人気プロジェクトで、SQLiteが軽量なトランザクション処理向けデータベースとして普及したのと同様に、分析(OLAP)向けの「組み込み型」データベースとして広く使われている。C++で実装され、サーバーのインストールや管理を必要とせずアプリケーションに直接組み込める点や、PythonのPandasライブラリなどと直接連携できる点が特徴だ。

買収後もDuckDB自体はMITライセンスの下でオープンソースとして提供され続け、独立したDuckDB Foundationがプロジェクトの統治を継続する。共同創業者のHannes MühleisenとMark Raasveldtは、アムステルダムを拠点にAWS社内でエンジニアリングチームを率い、技術的な方向性を主導していく。AWSのAndy Warfield副社長は「DuckDBは素晴らしいコミュニティを持つ優れたオープンソースプロジェクトであり、S3の顧客に広く使われ、愛されている」とコメントしている。

## 買収の狙いと技術的背景

DuckDBは、世界のSQLクエリの9割以上を占めるとされる1TB以下の中小規模データ分析に特化した設計で、ベクトル化実行エンジンによりコンパイルを介さずにクエリを高速処理できる点が強みだ。AWSはこのアーキテクチャを、S3やRedshiftといったエンタープライズ規模のサービスと統合し、特にAIエージェントがデータと対話する際の基盤として最適化したい考えを示している。両社の協業は今回が初めてではなく、2025年初頭にはAmazon S3 TablesおよびSageMaker LakehouseへのDuckDB統合が既に進められていた。実例として、Allen Instituteでは数分かかっていたクエリが1秒未満に短縮され、Amazon QuickではDuckDB統合により平均クエリレイテンシが30%削減されたという成果も報告されている。

## ガバナンスと業界への影響

オープンソースプロジェクトが大手クラウドベンダーに買収される事例では、コミュニティのガバナンスが特定企業の意向に左右されるのではないかという懸念が付きまとう。これに対しDuckLabsのMühleisen CEOは、DuckDB Foundationの役割を拡大し、新たに技術諮問委員会(Technical Advisory Board)を設置する方針を示した。これにより、DuckDBの拡張機能をエコシステムに組み込む他のクラウドベンダーや企業も、AWSとの利害対立を懸念することなくプロジェクトの方向性に関与できる仕組みを整えるとしている。DuckDBの拡張機能エコシステムについても、サードパーティによる署名付き拡張への対応拡大が計画されている。ライセンスと統治体制の独立性が実際にどこまで維持されるかは、今後のFoundationの運営体制が注目点となりそうだ。
