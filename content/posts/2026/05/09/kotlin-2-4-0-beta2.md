---
date: "2026-05-09T02:36:52+09:00"
title: "Kotlin 2.4.0 Beta2 — コンテキストパラメータ等がStable化、Wasm向けインクリメンタルコンパイルもデフォルト有効に"
description: "JetBrainsがKotlin 2.4.0のBeta2をリリースし、コンテキストパラメータや明示的バッキングフィールド、UUIDサポートのStable化に加え、Kotlin/Wasmのインクリメンタルコンパイルのデフォルト有効化やKotlin/NativeへのSwift Package Managerサポートなど多数の改善が含まれた。"
tags:
  - Programming Languages
references:
  - "https://blog.jetbrains.com/kotlin/2026/05/kodees-kotlin-roundup-golden-kodee-finalists-kotlin-2-4-0-beta2-and-new-learning-resources/"
  - "https://kotlinlang.org/docs/whatsnew-eap.html"
---

## 概要

JetBrainsは2026年4月22日、Kotlin 2.4.0のEarly Access Preview第2弾（Beta2）をリリースした。安定版のリリースは2026年6〜7月を予定しており、今回のBeta2では言語機能・標準ライブラリ・各プラットフォーム（JVM、Native、Wasm、JS）にわたる広範な改善が盛り込まれている。最大のポイントは、Experimentalステータスだった複数の機能がStableに昇格したことと、Kotlin/Wasmのインクリメンタルコンパイルがデフォルト有効化されたことだ。

## 言語機能の安定化と新機能

今回のリリースで最も注目されるのは、**コンテキストパラメータ（Context Parameters）** のStable昇格だ（呼び出し可能参照を除く）。コンテキストパラメータは関数シグネチャに暗黙的なコンテキストを宣言できる機能で、依存性の受け渡しを明示的に書くことなく表現できる。合わせて、**明示的バッキングフィールド（Explicit Backing Fields）** と **`@all` メタターゲット for properties** もStableとなった。

新たにExperimentalで追加された機能として、**明示的コンテキスト引数** が挙げられる。同名の関数が複数のコンテキスト型に対してオーバーロードされている場合に曖昧さを解消するための構文で、`sendNotification(emailSender = defaultEmailSender)` のように名前付きで指定できる。また、**コレクションリテラル**（`-Xcollection-literals` フラグ）も新たに導入され、`val fruit = ["apple", "banana", "cherry"]` のような簡潔な構文でリストを生成できるようになった。さらに、**コンパイル時定数の改善**（`-XXLanguage:+IntrinsicConstEvaluation`）として、文字列関数（`.lowercase()`・`.uppercase()`・`.trim()`）や符号なし型演算、enumの `.name` プロパティがコンパイル時に評価されるようになった。

## 標準ライブラリの変更

`kotlin.uuid.Uuid` APIがStableに昇格した（V4/V7生成関数を除く）。また、コレクションのソート順序を検証する新しい拡張関数群（`isSorted()`・`isSortedBy()`・`isSortedDescending()`・`isSortedWith()` など）が追加された。JVM向けには、符号なし整数（`ULong`、`UInt`）から `BigInteger` への変換関数も追加されている。

## プラットフォーム別の改善

**Kotlin/JVM** では Java 26 のバイトコード生成に対応し、Kotlinメタデータに保存されたアノテーションへのアクセスがデフォルトで有効化された。

**Kotlin/Native** では2つの大きな進展がある。GradleのビルドスクリプトからSwift Package Manager（SwiftPM）の依存関係を宣言できる **Swiftパッケージインポート** がExperimentalで追加された。また、**ガベージコレクタのデフォルトがCMS（Concurrent Mark Sweep）に変更** され、GCによる一時停止時間が短縮されてCompose Multiplatformなどのアプリでのレスポンスが向上する。さらに、**Swift Exportで `kotlinx.coroutines.Flow` をSwiftの `AsyncSequence` としてエクスポート** できるようになった。

**Kotlin/Wasm** では、インクリメンタルコンパイルがStableに昇格しデフォルト有効化された。大規模プロジェクトではビルド時間の大幅な短縮が見込まれる。また、**WebAssembly Component Model** への対応により、言語非依存なコンポーネント構成やFaaS（サーバーレス）アプリケーションでの活用が可能になった。

**Kotlin/JS** では、インライン `value class` をTypeScriptにエクスポートできるようになったほか、`js()` 関数内でアロー関数・ESクラス・テンプレート文字列・スプレッド演算子など主要なES2015構文が使用可能になった。

## 今後の展望

Kotlin 2.4.0の安定版は2026年6〜7月のリリースを予定している。今回Beta2でStableに昇格したコンテキストパラメータは、Kotlinのコードスタイルに大きな影響を与える機能であり、フレームワークやライブラリ側での対応が今後進むと見られる。Kotlin/Wasmの継続的な強化とKotlin Multiplatformのエコシステム拡充も着実に進んでおり、クロスプラットフォーム開発の選択肢としてのKotlinの地位がさらに高まりそうだ。
