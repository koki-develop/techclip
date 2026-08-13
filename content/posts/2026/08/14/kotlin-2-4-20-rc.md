---
date: "2026-08-14T08:13:07+09:00"
title: "Kotlin 2.4.20-RC公開、コルーチン例外のスタックトレース復元やWasmtime対応など多数の改善"
description: "JetBrainsがKotlin 2.4.20-RCを公開し、コルーチン例外のスタックトレース復元機能やコレクションの要素チェック関数、Kotlin/NativeのSwift Export強化、Wasmtimeランタイム対応などを追加した。"
tags:
  - Programming Languages
references:
  - "https://kotlinlang.org/docs/whatsnew-eap.html"
---

## 概要

JetBrainsは2026年8月12日、Kotlin 2.4.20のリリース候補版（RC）を公開した。今回のRCでは、標準ライブラリへのコルーチン例外のスタックトレース復元機能やコレクションの要素チェック関数の追加に加え、Kotlin/NativeにおけるSwift Exportの強化、Kotlin/Wasmでの新たなランタイム対応、Kotlin/JSのブラウザテスト刷新など、プラットフォーム横断で多数の改善が盛り込まれている。正式版へ向けた最終確認段階の位置づけで、IntelliJ IDEAやAndroid Studioを最新版に更新した上で、ビルドスクリプトのKotlinバージョンを`2.4.20-RC`に変更することで試用できる。

## 標準ライブラリの改善

コルーチンのデバッグ性向上を目的として、新たに`StackTraceRecoverable`インターフェースが導入された。これは、コルーチンが例外をスローして再送出する際に、例外に紐づくスタックトレースの復元方法をカスタマイズできるようにするもので、`copyForStackTraceRecovery()`メソッドを実装することで、例外の再構築ロジックを定義できる。利用には`@OptIn(ExperimentalStdlibCoroutineSupportApi::class)`によるオプトインが必要で、全ターゲットで利用可能だが、JVM上の`kotlinx.coroutines`ではすでに活用されている。

また、コレクション要素の性質を検証する実験的な関数として、`allDistinct()`（全要素が一意かを確認）、`allDistinctBy()`（指定したプロパティが一意かを確認）、`allEqual()`（全要素が同一かを確認）、`allEqualBy()`（指定したプロパティが全て同一かを確認）の4関数が新たに追加された。こちらも`@OptIn(ExperimentalStdlibApi::class)`が必要な実験的APIとなっている。

## Kotlin/Native・Wasm・JSの強化

Kotlin/NativeのSwift Exportでは、Kotlinのsealedクラス階層をSwiftのenumにマッピングし、Swift側で網羅的な`switch`文を書けるようになったほか、Swift側で実装したKotlinインターフェースをKotlin関数に渡す「逆方向インポート」パターンもサポートされ、プラットフォーム固有実装の受け渡しが容易になった。さらに`assembleSharedXCFramework`タスクがSwiftPM依存関係向けの`Package.swift`を自動生成するようになり、XCFrameworkの配布が簡素化される。

Kotlin/Wasmでは、Node.jsに加えて選択できる新たなスタンドアロンWebAssemblyランタイムとして、`wasmWasi`ターゲット向けにWasmtime対応が追加された。加えて、`@JsFun`宣言内でのトップレベル`require()`はコンパイルエラーとなり、`@JsModule`アノテーションや`import()`式への移行が求められるほか、コンパニオンオブジェクトの初期化順序がJVMと同様にスーパークラス優先へと変更され、プラットフォーム間の一貫性が向上した。Kotlin/JSでは非推奨となったKarmaに代わり、Mocha・Webpack・Playwrightを組み合わせた新しいブラウザテストDSLが実験的機能として導入され、Chromium・Firefox・WebKitでのテストに対応する。

## その他の変更点

Build Tools API（BTA）の対応範囲がKotlin/JS、Kotlin/Wasm、Kotlinメタデータにも拡大され、`gradle.properties`でのオプトインを経てKotlin 2.5.0でのデフォルト化が予定されている。また、標準の`kotlinc`より高速な起動とパフォーマンスを実現する、ネイティブコンパイライメージの初の実験的リリースも行われた。Serialization、Compose、All-openなど主要なコンパイラプラグインをバンドルしており、GitHub Releasesから入手できる。今回のRCは正式リリースに向けた最終検証段階であり、フィードバックを踏まえて安定版への反映が進められる見込みだ。
