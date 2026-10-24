---
date: "2026-10-25T08:09:48+09:00"
title: "Bun v1.4.4リリース、Prettier互換の高速フォーマッタ「bun fmt」と型チェッカーの大幅高速化を実現"
description: "JavaScriptランタイムBunがv1.4.4をリリースし、Prettier互換の新フォーマッタ「bun fmt」や型チェッカー「bun check」の大幅な高速化、Yarn Berryロックファイルの移行サポートなどを追加した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://bun.com/blog/bun-v1.4.4"
---

## 概要

JavaScript/TypeScriptランタイムのBunは10月22日、v1.4.4をリリースした。今回の目玉は新コマンド`bun fmt`で、Prettierの設定ファイル（`.prettierrc`や`prettier.config.*`など）やoxfmt形式の設定をそのまま読み込める互換フォーマッタとして実装された。JavaScript、TypeScript、JSX、CSS、HTML、Vue、Svelte、JSON、YAML、Markdown、GraphQLなど幅広い言語に対応し、インポートの並び替えやTailwind CSSのクラス順序の整理も別プラグインなしで組み込みで行える。Prettier自身のリポジトリ（2,616ファイル）を対象にした計測では、Prettier 3.9.10が17.1秒かかる処理を`bun fmt`は59.7ミリ秒で完了し、286倍の速度を記録した。Prettierの9,731件のテストケースに対する互換性も99.1%に達しているという。Git連携用に`bun fmt --check`、`bun fmt --staged`、`bun fmt --changed`といったオプションも用意されている。

## 型チェッカーとパッケージ管理の強化

組み込み型チェッカー`bun check`も大幅に高速化された。大規模プロジェクトで1.4〜7.8倍の速度向上が確認されており、MUIのドキュメントサイトでは検証時間が10.28秒から1.31秒に短縮、ピークメモリ使用量も11.2GBから1.3GBへ大幅に削減されている。複数プロジェクトを扱う`bun check -b`では、パース結果の共有により最大15.7倍の高速化を実現したとしている。

パッケージ管理の面では、Yarn 2以降（Yarn Berry）のロックファイルを`bun.lock`形式に変換するマイグレーション機能が追加された。バージョン固定やワークスペース構成、`npm:`エイリアス、`resolutions`、Git・tarball・`file:`依存、`patch:`依存（`patchedDependencies`への変換）まで保持される。加えて、インストール失敗時に50〜800msの間隔で指数バックオフ再試行を行う仕組みや、ウォームキャッシュ時にLinuxで最大3.2倍速くなる並列リンク処理（8スレッド）、pnpmに近い挙動となったピア依存解決ロジックなども導入された。新コマンドとして、`node_modules`を作らずに依存関係だけを取得する`bun pm fetch`、キャッシュを管理する`bun pm cache pack/unpack/prune`、モノレポ全体を依存順に公開する`bun publish --recursive`も追加されている。

## データベース・WebSocket・ランタイムの改善

`Bun.SQL`はPostgreSQLでクエリあたりのCPU命令数を21〜48%削減し、MySQLでの一括挿入でも53%の命令数削減を実現した。PostgreSQLのクエリでは1回あたりのオブジェクト割り当ても84個から28個に減少している。機能面では、PostgreSQLの`COPY`ストリームのバックプレッシャー対応、`SQL.camel`・`SQL.pascal`などのカラム名変換、JavaScript配列とPostgreSQL配列カラムの直接マッピングなどが加わった。SQLiteでも`db.function()`や`db.aggregate()`によるユーザー定義関数、`db.onInsert`などの更新フックが利用可能になっている。

`ws`パッケージの互換性も改善され、npm版の`ws`テストスイート271件中234件が成功するようになった（従来は94件）。`createWebSocketStream()`のバックプレッシャー対応やSOCKSプロキシ経由の接続、ブラウザに合わせたクローズハンドシェイクの実装なども行われている。さらに、JavaScriptCoreエンジンにWebKitの最新コミット1,013件を取り込んだことで、`toLocaleString()`が10万回呼び出しで54倍高速化（1,341msから25msへ）し、100万要素の配列読み込みも4.2倍速くなった。開発体験の面では、Devサーバーのエラーオーバーレイがシステムのライト/ダークテーマに追従するよう再設計され、類似エラーのグルーピング表示にも対応している。
