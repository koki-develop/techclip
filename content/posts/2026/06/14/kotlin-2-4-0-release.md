---
date: "2026-06-14T02:35:04+09:00"
title: "Kotlin 2.4.0正式リリース——Java 26対応、Swift Package統合、Wasm Component Modelなどマルチプラットフォーム強化"
description: "JetBrainsがKotlin 2.4.0を正式リリースし、Java 26サポートやSwift Packagesの依存関係統合、WebAssembly Component Model対応、CMS GCのデフォルト有効化など多数の強化が施された。"
tags:
  - Programming Languages
references:
  - "https://blog.jetbrains.com/kotlin/2026/06/kotlin-2-4-0-released/"
  - "https://blog.jetbrains.com/idea/2026/06/java-annotated-monthly-june-2026/"
---

## 概要

JetBrainsは2026年6月3日、Kotlin 2.4.0を正式リリースした。本リリースは言語機能の安定化、標準ライブラリの拡充、そして各プラットフォームターゲット（JVM・Native・Wasm・JS）にわたる包括的な改善を含んでいる。特にKotlin Multiplatform（KMP）エコシステムの強化が今回の目玉であり、Swift PackagesやWebAssemblyの最新仕様への対応によってクロスプラットフォーム開発の幅がさらに広がった。

## 言語機能と標準ライブラリ

言語レベルでは、コンテキストパラメーター（Context Parameters）と明示的なバッキングフィールド（Explicit Backing Fields）がStable（安定版）に昇格した。アノテーションの使用サイトターゲット機能も複数追加されており、より細粒度なアノテーション制御が可能になった。標準ライブラリではUUID APIのサポートが安定化し、コレクションのソート順序チェック機能も新たに提供されている。

## プラットフォーム別の強化

**Kotlin/JVM**では、最新のJava 26への対応が実現した。また、メタデータ内のアノテーションがデフォルトで有効化されており、リフレクションやフレームワーク連携の利便性が向上する。ビルドツール面ではGradle 9.5.0との互換性が確保され、Mavenではカスタム設定なしにJavaとJVMターゲットバージョンの自動整合が機能するようになった。

**Kotlin/Native**では、Swift Packagesを依存関係として直接サポートする機能が追加され、iOSやmacOSをターゲットとするKMPプロジェクトのライブラリ管理が大幅に簡素化された。またConcurrent Mark-Sweep（CMS）ガベージコレクターがデフォルトで有効化され、ネイティブアプリケーションのパフォーマンスと応答性が改善される。

**Kotlin/Wasm**ではインクリメンタルコンパイルがデフォルトで有効になり、ビルド時間の短縮が期待できる。さらにWebAssembly Component Modelのサポートが追加されたことで、Wasm同士のコンポーネント間連携やホスト環境との相互運用性が向上し、ブラウザ外でのWasm活用シナリオが広がった。**Kotlin/JS**では値クラスのエクスポートとES2015機能のインライニング対応が実装されている。

## エコシステムの動向

Java Annotated Monthly（2026年6月号）によると、KotlinConf'26のキーノートでは複数のエコシステムアップデートが発表されており、AIエージェント向けSDK「Koog 1.0」の安定リリースや、Visual Studio Code向けKotlin公式サポートのアルファ版提供開始なども注目を集めた。Kotlin 2.4.0は最新のIntelliJ IDEAまたはAndroid Studioに同梱されており、既存プロジェクトはビルドスクリプトのKotlinバージョンを2.4.0に更新するだけで移行できる。
