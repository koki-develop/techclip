---
date: "2026-07-18T02:27:18+09:00"
title: "PostgreSQL 19ベータ2がリリース、グラフクエリとゼロダウンタイム再編成を正式ロードマップに"
description: "PostgreSQLプロジェクトがバージョン19の2回目のベータ版を公開し、SQL/PGQによるネイティブグラフクエリや統合REPACKコマンドなど機能凍結後の安定化が進んでいることを示した。"
tags:
  - OSS
references:
  - "https://www.postgresql.org/about/news/postgresql-19-beta-2-released-3350/"
---

## 概要

PostgreSQLプロジェクトは7月16日、次期メジャーバージョンとなる「PostgreSQL 19」の2回目のベータ版「Beta 2」をリリースした。すでに機能凍結（feature freeze）を迎えており、今回のBeta 2ではvacuumdbの`--analyze-in-stages`オプションがパーティションテーブルで正しく動作しない不具合や、ロジカルデコーディングの競合状態、REPACKワーカーがFATALエラー時にクリーンアップされない問題など、14件のバグ修正と改善が取り込まれた。正式リリースは2026年9月〜10月頃を予定しており、必要に応じて追加のベータ版やリリース候補版（RC）が提供される見込みだ。プロジェクト側は本番環境での利用は推奨しておらず、ワークロードでの動作検証とフィードバックをコミュニティに呼びかけている。

## 目玉機能：SQL/PGQによるネイティブグラフクエリ

PostgreSQL 19の目玉機能の一つが、SQL標準の一部であるSQL Property Graph Queries（SQL/PGQ）のサポートだ。これにより、専用のグラフデータベース拡張を使わずとも、標準SQLの枠組みの中でグラフ構造データをクエリできるようになる。実装上はビューと同様に内部的に処理され、通常のリレーショナルクエリとして書き下される点が特徴で、Peter Eisentraut氏やAshutosh Bapat氏らが開発に貢献した。Beta 2ではこの機能自体にも複数の不具合修正が加えられており、安定化が進んでいる段階にある。

## ゼロダウンタイムのテーブル再編成を実現する統合REPACKコマンド

もう一つの主要な変更が、`VACUUM FULL`と`CLUSTER`を置き換える統合コマンド`REPACK`の追加だ。`REPACK [table_name] [CONCURRENTLY]`という構文で実行でき、`CONCURRENTLY`オプションを指定するとアクセス排他ロックを取得せずにテーブルを再構築できるため、運用中のシステムでもダウンタイムなしにテーブル再編成が可能になる。同時実行される再編成処理の数を制御する新しいサーバ変数`max_repack_replication_slots`も追加された。従来の`VACUUM FULL`や`CLUSTER`コマンド自体は後方互換性のため引き続き利用できる。開発にはAntonin Houska氏、Mihail Nikalayeu氏、Álvaro Herrera氏らが携わった。

## その他の主要な変更点

PostgreSQL 19では、この他にも幅広い改善が予定されている。時系列データを扱う`FOR PORTION OF`構文による時間範囲指定の`UPDATE`/`DELETE`、`ALTER TABLE ... MERGE/SPLIT PARTITIONS`によるパーティションの結合・分割、ロジカルレプリケーションにおけるシーケンス値の同期やパブリケーションからの除外指定（`FOR ALL TABLES EXCEPT`）などが含まれる。パフォーマンス面では、autovacuumの並列化、COPY処理でのSIMD命令活用、TOASTのデフォルト圧縮方式を`pglz`から`lz4`へ変更するなどの最適化が図られている。一方で、JITがデフォルトで無効化される、RADIUS認証のサポートが削除される、`max_locks_per_transaction`のデフォルト値が64から128に引き上げられるといった、既存環境への影響を伴う変更点も含まれている。

## 今後の見通し

機能凍結後のこの段階では大きな新機能の追加は見込まれず、今後のベータ版やRCではバグ修正と安定化が中心となる。正式版は2026年9月から10月にかけてリリースされる予定で、テストユーザーには[未解決課題一覧](https://wiki.postgresql.org/wiki/PostgreSQL_19_Open_Items)の確認や、[バグ報告フォーム](https://www.postgresql.org/account/submitbug/)を通じたフィードバックが呼びかけられている。グラフクエリのネイティブサポートやゼロダウンタイムのテーブル再編成は、大規模運用環境やアナリティクス用途において注目度の高い機能であり、正式リリースに向けた今後の検証状況が引き続き注視される。
