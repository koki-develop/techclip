---
date: "2026-11-20T18:09:22+09:00"
title: "PostgreSQL 19が正式リリース、無停止デフラグの「REPACK」や実行計画安定化機能を追加"
description: "PostgreSQL 19が正式リリースされ、無停止でテーブルを再編成する「REPACK」コマンドや実行計画を安定化する「pg_plan_advice」などミッションクリティカル運用向けの新機能が多数追加された。"
tags:
  - OSS
references:
  - "https://www.postgresql.org/about/news/postgresql-19-released-3449/"
  - "https://forest.watch.impress.co.jp/docs/news/2158045.html"
---

## 概要

PostgreSQLグローバル開発グループは11月19日、新メジャーバージョン「PostgreSQL 19」を正式リリースした。今回のリリースはミッションクリティカルなワークロードにおける運用・開発の簡素化を軸に据えており、最大の目玉は無停止でテーブルの肥大化（bloat）を解消する新コマンド「REPACK」だ。従来の`VACUUM FULL`や`CLUSTER`はテーブル全体をロックしてしまうため、本番運用中のメンテナンスが難しかったが、`REPACK (CONCURRENTLY)`を使えば処理の大部分で読み書きを継続しながら未使用領域を回収し、インデックスに合わせてデータを再配置できる。既存の`VACUUM FULL`と`CLUSTER`も互換性のため残されている。サポート期間は2031年11月19日までで、旧バージョンのPostgreSQL 14は11月12日にサポートを終了している。

## 実行計画の安定化とグラフクエリ対応

もう一つの大きな柱が、クエリ実行計画の安定化だ。新拡張機能「pg_plan_advice」は"plan advice"と呼ばれるミニ言語でプラン選択を実験・固定できるようにするもので、これと連携する「pg_stash_advice」を組み合わせることで、アプリケーション側のコードを変更せずにクエリ識別子ベースで遅い実行計画を自動修正できるようになった。データ変更によって実行計画が不意に変わり性能が劣化する、という運用上よくある問題に対する直接的な解決策といえる。

## 並列autovacuumと論理レプリケーションの強化

バックグラウンドメンテナンスの面では、autovacuumの並列処理が強化された。新設定`autovacuum_max_parallel_workers`でインデックスの真空処理に使うワーカー数を制御できるようになり、テーブルごとの処理優先度を決める新しいスコアリングシステムも導入された。あわせて`pg_stat_lock`や`pg_stat_recovery`、`pg_stat_autovacuum_scores`といった監視用ビューが追加され、運用の可視性が向上している。論理レプリケーションでは、`CREATE PUBLICATION ... FOR ALL SEQUENCES`によりシーケンス値の自動複製が可能になったほか、`FOR ALL TABLES`に特定テーブルを除外する`EXCEPT`句、`postgres_fdw`などの外部サーバーから接続設定を取得する`SERVER`句が追加された。分散システム向けには、スタンバイ側でプライマリへの書き込み完了を待機できる`WAIT FOR LSN`も新設され、読み取り一貫性(read-your-writes)を実現しやすくなっている。

## パフォーマンスとその他の改善

クエリ性能では、外部キー制約チェックの最適化によりバルク挿入が約2倍高速化したほか、`NOT IN`のアンチジョイン変換やジョイン前に集約を行う先行集約(eager aggregation)など、オプティマイザの改善も多数取り込まれた。開発者向けには「get or create」パターンを簡潔に書ける`INSERT ... ON CONFLICT DO SELECT`や、JSON形式での`COPY`出力対応が加わっている。セキュリティ面ではサーバー側のSNI(Server Name Indication)に対応し、ホスト名ごとに異なるTLS証明書を提示できるようになった一方、md5認証には警告が発行されるようになり、RADIUS認証は削除、JITコンパイルはデフォルトで無効化されるなど、非推奨機能の整理も進んだ。REPACKやpg_plan_adviceのような運用負荷を下げる機能群は、大規模システムでの無停止運用をさらに後押しするものとして注目される。
