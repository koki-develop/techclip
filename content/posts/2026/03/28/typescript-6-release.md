---
date: "2026-03-28"
title: "TypeScript 6.0正式リリース、JavaScript実装最後のメジャー版でGo製7.0への橋渡しに"
description: "MicrosoftがTypeScript 6.0を正式リリースし、現行のJavaScriptベースコンパイラとしては最後のメジャーバージョンとなるこのリリースで、Go言語で再実装される7.0への移行準備が本格化した。"
tags:
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/typescript/announcing-typescript-6-0/"
  - "https://www.heise.de/en/news/TypeScript-6-0-is-ready-On-the-way-to-Go-based-TypeScript-7-0-11222392.html"
  - "https://www.infoworld.com/article/4149659/typescript-6-0-arrives.html"
---

## 概要

Microsoftは2026年3月23日、TypeScript 6.0を正式にリリースした。本バージョンは、現行のJavaScriptで書かれたコンパイラによる最後のメジャーリリースであり、Go言語で全面的に再実装される次期TypeScript 7.0（Project Corsa）への「橋渡し」となる重要なリリースと位置付けられている。プリンシパルプロダクトマネージャーのDaniel Rosenwasser氏は「TypeScript 7.0は完成に極めて近い状態にある」と述べ、6.0を導入したプロジェクトにはネイティブプレビュー版の7.0も試すよう呼びかけている。

## 主な新機能と改善点

TypeScript 6.0では、ES2025ターゲットのサポートが追加され、`RegExp.escape()`、Temporal API（Stage 4到達）、`Promise.try`、Iteratorメソッド、Setメソッドなどの型定義が利用可能になった。特にTemporal APIは、JavaScriptにおける日付・時刻処理の長年の課題を解決するものとして注目されており、`Temporal.Now.instant()`などの操作がTypeScriptの型安全性のもとで利用できるようになる。ブラウザ側ではFirefox 139以降、Chrome 144以降で対応している。

型推論の面では、`this`を使用しない関数における文脈依存性が緩和され、プロパティの宣言順序に関係なく型パラメータの推論が改善された。また、ジェネリックJSX式における関数式の型チェックも強化されている。モジュール解決では、Node.js 20以降で利用可能な`#/`プレフィックスによるサブパスインポートのサポートや、`--moduleResolution bundler`と`--module commonjs`の組み合わせが可能になった。DOM型ライブラリでは、`dom.iterable`と`dom.asynciterable`の内容が`dom`に統合され、設定がシンプルになった。

## デフォルト設定の大幅な変更

6.0ではデフォルト設定が大きく変更されている。`strict`がデフォルトで`true`に、`module`が`esnext`に、`target`が`es2025`にそれぞれ変更された。また、`types`がデフォルトで空配列となり`@types`パッケージの自動検出が行われなくなったため、`"types": ["node"]`などの明示的な指定が必要になる。`rootDir`もデフォルトで`.`（tsconfig.jsonのあるディレクトリ）に固定され、推論されなくなった。

## 非推奨機能とTypeScript 7.0への移行

多くのレガシーオプションが非推奨または削除された。`target: es5`、`--moduleResolution node`（`nodenext`や`bundler`への移行を推奨）、`--baseUrl`などは非推奨となり、一時的に`"ignoreDeprecations": "6.0"`で抑制できるが、7.0では完全に削除される予定だ。一方、`--module amd/umd/systemjs`や`--outFile`は6.0で既に削除されている。また、import assertion構文（`assert`）の非推奨が`import()`呼び出しにも拡大され、`with`構文への移行が求められる。

7.0への移行を支援する`--stableTypeOrdering`フラグも導入された。6.0では型IDが出現順に割り当てられるが、7.0では決定論的なコンテンツベースのソートが採用されるため、このフラグで事前に挙動を揃えることができる。ただし型チェックが最大25%遅くなるため、あくまで診断用途であり、本番利用は推奨されていない。TypeScript 7.0のネイティブプレビューはVisual Studio Code拡張およびnpmパッケージ（`@typescript/native-preview`）として既に利用可能で、ネイティブコード速度と共有メモリマルチスレッドによる大幅なパフォーマンス向上が期待されている。
