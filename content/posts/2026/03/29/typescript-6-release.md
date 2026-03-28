---
date: "2026-03-29"
title: "TypeScript 6.0正式リリース、JavaScriptベース最終版としてGo製コンパイラへの移行準備が本格化"
description: "MicrosoftがTypeScript 6.0を正式リリースし、JavaScriptベースの最後のメジャーバージョンとして多数のデフォルト変更・非推奨化を導入、Go実装のTypeScript 7.0への移行を促している。"
tags:
  - Programming Languages
references:
  - "https://visualstudiomagazine.com/articles/2026/03/23/typescript-6-0-ships-as-final-javascript-based-release-clears-path-for-go-native-7-0.aspx"
---

## 概要

Microsoftは2026年3月23日、TypeScript 6.0を正式にリリースした。本バージョンは現行のJavaScriptベースコンパイラで構築される最後のメジャーリリースであり、Go言語で再実装されるTypeScript 7.0への橋渡しとなる重要なマイルストーンである。TypeScript 6.0では9つのデフォルト設定が一斉に変更され、複数のレガシーオプションが非推奨または削除となったため、アップグレード時には`tsconfig.json`の見直しが必須となる。

## 主要な新機能

TypeScript 6.0では、TC39 Stage 4に到達した複数の提案に対する型サポートが追加された。`Temporal` APIのビルトイン型が利用可能になり、日時操作がネイティブにサポートされる。また、`Map`と`WeakMap`に`getOrInsert`/`getOrInsertComputed`メソッドが追加され、upsertパターンのボイラープレートが削減された。`RegExp.escape`や`Promise.try`、Iteratorメソッド、Setメソッドを含む`es2025`ターゲットも新たにサポートされている。

さらに、Node.jsのサブパスインポートで`#/`プレフィックスが利用可能になり、`nodenext`および`bundler`モジュール解決で対応する。`bundler`解決戦略と`--module commonjs`の組み合わせも可能になり、非推奨となった`node`解決からの移行パスが提供されている。

## 破壊的変更とデフォルト設定の刷新

今回のリリースでは多数のデフォルト値が変更された。`strict`は`true`に、`module`は`esnext`に、`target`は`es2025`にそれぞれ変更され、`types`はすべての`@types`パッケージを自動的に読み込む代わりに空配列`[]`がデフォルトとなった。この`types: []`への変更により、コールドビルド時間が最大50%改善されるケースも報告されている。

レガシーオプションについては、`target: es5`の非推奨化（最小サポートはES2015）、`outFile`の削除、`moduleResolution: node`の非推奨化（`nodenext`または`bundler`への移行を推奨）、`module Foo {}`構文のエラー化（`namespace`キーワードへ移行）、`moduleResolution: classic`の完全削除など、大規模な整理が行われた。インポートアサーション構文も`assert`から`with`への移行が必要となる。

これらの非推奨オプションは`"ignoreDeprecations": "6.0"`を設定することで一時的に警告を抑制できるが、TypeScript 7.0では完全に削除される予定だ。

## Go製コンパイラ「Project Corsa」とTypeScript 7.0への展望

TypeScript 7.0の基盤となるGo実装コンパイラは「Project Corsa」と呼ばれ、バイナリ名は`tsgo`、GitHubの`microsoft/typescript-go`リポジトリで開発が進められている。ネイティブコードの高速性と共有メモリマルチスレッディングを活用し、劇的なパフォーマンス改善が実現されている。VS Codeの150万行のコードベースにおいて、型チェック時間が77秒から7.5秒へと約10倍高速化され、プロジェクトの読み込みも8倍速くなり、メモリ使用量は半減した。

TypeScript 6.0には、7.0との動作差異を検出するための`--stableTypeOrdering`フラグも導入されており、型の順序を決定的にすることで移行時の互換性確認を支援する（ただし最大25%のオーバーヘッドが発生する）。Go製コンパイラはすでにVS Codeプレビュー拡張機能およびnpmの`@typescript/native-preview`パッケージとして利用可能で、チームは「完成に極めて近い」状態だとしている。安定版リリースは2026年後半から2027年初頭が見込まれている。

TypeScriptチームは、開発者に対してまずTypeScript 6.0へのアップグレードを行い、段階的に移行を進めることを推奨している。7.0のリリース時にまとめて対応するよりも、今から準備を始める方が負担が少ないという方針だ。
