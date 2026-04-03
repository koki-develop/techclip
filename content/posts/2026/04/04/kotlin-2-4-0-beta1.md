---
date: "2026-04-04T02:16:45+09:00"
title: "Kotlin 2.4.0-Beta1リリース：コンテキストパラメーターが安定化、Swift Packageサポートも追加"
description: "Kotlin 2.4.0-Beta1がリリースされ、コンテキストパラメーターの安定化、UInt/ULongからBigIntegerへの変換API、Swift PackageをKotlin/Nativeの依存関係として利用する実験的機能など多数の改善が含まれた。"
tags:
  - Programming Languages
references:
  - "https://kotlinlang.org/docs/whatsnew-eap.html"
---

## 概要

2026年3月31日、Kotlin 2.4.0-Beta1がリリースされた。今回のリリースでは、言語機能・標準ライブラリ・Kotlin/JVM・Kotlin/Native・コンパイラの各分野にわたる改善が行われている。最大のハイライトは、Kotlin 2.2.0で実験的機能として導入されたコンテキストパラメーターが正式に安定化（Stable）されたことだ。ただし、コンテキスト引数（context arguments）とcallable referencesについては引き続き安定版ではない。

## 言語機能の強化

コンテキストパラメーターの安定化に加え、アノテーションのuse-siteターゲットに関する機能群も安定化された。また、実験的機能として「明示的コンテキスト引数（Explicit context arguments）」が追加された。Kotlin 2.3.20でのオーバーロード解決の変更により、コンテキストパラメーターだけが異なる複数のオーバーロードが曖昧になる問題が発生していたが、この新機能により呼び出し側で明示的にコンテキストを指定することで解消できるようになった。この機能はコンパイラフラグ `-Xexplicit-context-arguments` で有効化できる。

## 標準ライブラリの新API

標準ライブラリには2つの安定版APIが追加された。1つ目は、JVM向けに `UInt.toBigInteger()` と `ULong.toBigInteger()` の拡張関数が追加されたことで、文字列を経由するワークアラウンドなしに符号なし整数を `BigInteger` へ直接変換できるようになった。2つ目は、ソート順の検証をサポートする拡張関数群（`isSorted()`・`isSortedDescending()`・`isSortedWith()`・`isSortedBy()`・`isSortedByDescending()`）で、イテラブル・配列・シーケンスに対応し、最初の順序違反を検出した時点で処理を短絡するため効率的だ。

## Kotlin/JVMとKotlin/Nativeの改善

Kotlin/JVMでは、Java 26バイトコードをターゲットとしたクラスファイルの生成がサポートされた。また、Kotlin 2.2.0で導入されたKotlinメタデータへのアノテーション書き込み機能がデフォルト有効化され、アノテーションプロセッサーやツールがリフレクションやソースコード変更なしにアノテーション情報にアクセスできるようになった。Kotlin/Nativeでは、Swift PackageをGradle依存関係として宣言できる実験的機能が追加された。これにより、Kotlin Multiplatformプロジェクトのビルドスクリプト内で直接FirebaseなどのiOS向けライブラリを指定できるようになり、CocoaPodsからの移行ガイドも提供されている。

## コンパイラの改善：klibのインライン化挙動が統一

Kotlin/Native・Kotlin/JS・Kotlin/Wasmでの `.klib` コンパイル時のインライン化挙動が改善された。従来これらのターゲットでは、インライン関数の展開はバイナリ生成時のみ行われていたが、今回から同一モジュール内のインライン関数については `.klib` コンパイル段階でもインライン化されるようになった（クロスモジュールのインライン化は引き続きバイナリ生成時）。これにより、Kotlin/JVMでのインライン化挙動との統一に向けた第一歩となる。問題が発生した場合は `-Xklib-ir-inliner=disabled` で無効化でき、将来リリース予定のフルクロスモジュールインライン化は `-Xklib-ir-inliner=full` でプレビューできる。
