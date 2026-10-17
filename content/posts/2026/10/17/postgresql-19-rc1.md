---
date: "2026-10-17T18:12:03+09:00"
title: "PostgreSQL 19の最初のリリース候補版RC1が公開、GAは11月19日に"
description: "PostgreSQLコミュニティがメジャーバージョン19の最初のリリース候補RC1を公開し、Amazon RDSのプレビュー環境でも利用可能になった。"
tags:
  - OSS
  - Cloud
references:
  - "https://www.postgresql.org/about/news/postgresql-19-rc-1-released-3409/"
  - "https://aws.amazon.com/about-aws/whats-new/2026/10/postgresql-19-rc1-amazon-rds-database-preview-environment/"
---

## 概要

PostgreSQLコミュニティは10月15日、メジャーバージョン19の最初のリリース候補(RC1)を公開した。正式リリース(GA)は11月19日に予定されており、その前に11月12日には定例の更新リリースに合わせてRC2もリリースされる計画だ。同日、Amazon RDSの「Database Preview Environment」でもPostgreSQL 19 RC1が利用可能になり、ユーザーは本番導入前にUS East (Ohio)リージョンで新バージョンの動作を事前検証できるようになった。世界で広く使われるオープンソースデータベースの次期メジャーリリースが、着実に最終段階へと進んでいることを示す節目といえる。

## RC1での主な修正点

Beta 4以降、RC1では複数の不具合修正が加えられている。テーブルやインデックスを再構築する`REPACK (CONCURRENTLY)`、クエリ実行計画のヒント機能である`pg_plan_advice`に関する修正のほか、NULL式の扱いに関するクエリプランナの最適化も行われた。論理レプリケーションでは、`wal_level`が`replica`に設定されている場合の自動有効化に関する修正が入っている。また、`postgres_fdw`の統計情報収集が、従来のANALYZE実行ユーザーではなく外部テーブルの所有者権限で実行されるよう変更された。並列autovacuumについても複数の修正が加えられ、AWSの発表でも「複雑なテキスト検索式のエラー処理の改善」「並列autovacuumの堅牢化」「GINインデックスメンテナンスの信頼性向上」が安定性強化のポイントとして挙げられている。細かな変更点として、`COPY (query) TO ... (FORMAT json)`でJSON出力する際のキー名が、テーブルの列名ではなくクエリ側の列名・エイリアスを使用するようになった点も実務上の影響が大きい。

## 検証方法とAmazon RDSでの提供

PostgreSQLコミュニティはRC1の実機検証を呼びかけており、公式ダウンロードページから入手できるほか、不具合はバグ報告フォームから報告できる。リリース告知自体への訂正提案はpgsql-wwwメーリングリストで受け付けている。未解決の課題は「PostgreSQL 19 Open Items」のWikiページで追跡されている。アップグレードには`pg_upgrade`または`pg_dump`/`pg_restore`によるメジャーバージョンアップグレード手順を用いる。

一方、AWSはAmazon RDS Database Preview Environment経由でRC1を提供し、通常のRDS for PostgreSQLと同料金で試用できるようにした。ただしプレビュー環境のDBインスタンスは最大60日間で自動削除され、作成したスナップショットもプレビュー環境内でのみ利用可能という制約がある。データを環境外に持ち出す場合はPostgreSQLのダンプ・ロード機能を使う必要がある。

## 今後の見通し

RC2が11月12日、GAが11月19日とスケジュールが明示されたことで、PostgreSQL 19は最終準備段階に入ったことが明確になった。クラウド各社がGA前からプレビュー環境を用意し始めている点は、ユーザー企業にとって本番移行前の検証期間を確保しやすくなるという意味で歓迎される動きだ。今後RC2までに追加の修正が入る可能性もあるため、本番導入を検討しているユーザーはOpen Itemsページや公式アナウンスを継続的にチェックしておくとよいだろう。
