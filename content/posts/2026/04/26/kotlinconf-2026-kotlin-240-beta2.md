---
date: "2026-04-26T02:18:39+09:00"
title: "Kotlin 2.4.0-Beta2リリース：コレクションリテラル実験的導入、コンテキストパラメーターと明示的バッキングフィールドが安定化"
description: "KotlinConf 2026の開催に合わせてJetBrainsがKotlin 2.4.0-Beta2をリリースし、コンテキストパラメーターや明示的バッキングフィールドの安定化とコレクションリテラル構文の試験導入を発表した。"
tags:
  - Programming Languages
references:
  - "https://kotlinlang.org/docs/whatsnew-eap.html"
  - "https://blog.jetbrains.com/kotlin/2026/04/kotlinconf26-kotlin-2-4-0-beta2-and-the-latest-kotlin-ecosystem-news/"
---

## 概要

JetBrainsは2026年4月22日、ドイツ・ミュンヘンで5月20〜22日に開催されるKotlinConf 2026に合わせてKotlin 2.4.0-Beta2をリリースした。今回のベータ版では、これまで実験的だった複数の言語機能が安定版に昇格するとともに、コレクションリテラル構文など新たな実験的機能が追加されている。

安定化した主な機能としては、**コンテキストパラメーター**（コンテキスト引数や呼び出し可能参照を除く）、**明示的バッキングフィールド**、プロパティへの`@all`メタターゲット、ユースサイトアノテーションターゲットのデフォルトルール変更が挙げられる。また標準ライブラリの`kotlin.uuid.Uuid` APIも安定版となり、オプトインなしで使用できるようになった。

## 新しい実験的言語機能

**コレクションリテラル**は今回のベータ2で最も注目される実験的追加機能で、ブラケット構文`[]`を使ってコレクションを直感的に生成できる。型を明示すれば`MutableList`などの可変コレクション、型なしなら`List`がデフォルトとなる。`operator fun of`を定義したカスタム型でもこの構文を利用可能だが、Javaで定義されたコレクション型への適用は現時点で未サポート。有効化には`-Xcollection-literals`コンパイラフラグが必要だ。

**コンテキスト引数の明示指定**（`-Xexplicit-context-arguments`）も実験的に追加された。コンテキストパラメーターの違いだけでオーバーロードが存在する場合に、`sendNotification(emailSender = defaultEmailSender)`のように明示的にどのコンテキストを渡すか指定できるため、あいまいさを排除できる。さらに**コンパイル時定数の評価強化**も試験導入され、符号なし型の演算や文字列の`.lowercase()`/`.uppercase()`/`.trim()`、列挙型の`.name`プロパティなどをコンパイル時に評価できるようになった。

## 標準ライブラリと各プラットフォームの強化

標準ライブラリでは、ソート順チェック用の拡張関数群（`.isSorted()`、`.isSortedBy()`、`.isSortedDescending()`など）がイテラブル・配列・シーケンスに追加された。JVM向けには`UInt.toBigInteger()`と`ULong.toBigInteger()`が新設され、符号なし整数を`BigInteger`へ変換できる。またJava 26のバイトコード生成サポートと、Kotlinメタデータへのアノテーション格納がデフォルト有効化された。

Kotlin/Nativeでは、GradleからSwiftパッケージを依存関係として宣言するAPI（CocoaPodsからの移行ツール付き）が追加された。Swift Exportで`kotlinx.coroutines.Flow`をSwiftの`AsyncSequence`としてエクスポートできるようになり、型情報も保持される。またデフォルトGCがPMCS（Parallel Mark Concurrent Sweep）からCMS（Concurrent Mark and Sweep）に変更され、マーキングフェーズのアプリケーションスレッドとの並行実行によりGCポーズが大幅に短縮された。

Kotlin/Wasmでは2.1.0から導入されていたインクリメンタルコンパイルが安定版となりデフォルト有効化されたほか、FaaSやサーバーレス用途を想定したWebAssembly Component Modelへの実験的サポートが追加された。Kotlin/JSでは、インライン値クラスをTypeScriptのクラスとしてエクスポートする機能と、`js()`呼び出し内でES2015機能（アロー関数、スプレッド演算子、`const`/`let`など）をフルサポートするようになった。

## 今後の展望

KotlinConf 2026はミュンヘンで5月20〜22日に開催され、ワークショップやセッション、基調講演が予定されている。Kotlin 2.4.0の正式リリースに向けて、今回の実験的機能へのフィードバックが求められている段階だ。IDEサポートはIntelliJ IDEAおよびAndroid Studioの最新版に含まれており、ビルドスクリプトのKotlinバージョンを`2.4.0-Beta2`に変更することで試用できる。
