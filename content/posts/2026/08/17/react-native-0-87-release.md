---
date: "2026-08-17T02:03:41+09:00"
title: "React Native 0.87リリース、Strict TypeScript APIが標準化しSwift Package Manager対応も追加"
description: "React Native 0.87がリリースされ、Strict TypeScript APIのデフォルト有効化、Metro大幅高速化、iOS向けSwift Package Manager実験サポート、Android Gradle Plugin 9対応が実現した。"
tags:
  - Programming Languages
references:
  - "https://reactnative.dev/blog/2026/08/11/react-native-0.87"
---

## 概要

React Nativeチームは8月11日、最新版となる「React Native 0.87」をリリースした。今回の目玉は、型定義をソースコードから自動生成する「Strict TypeScript API」がデフォルトで有効化されたことだ。従来は手動管理されていた型定義とライブラリ実装のズレが解消され、`react-native`のルートエクスポートに対して安定した型情報が提供されるようになる。あわせて、ビルドツールMetroが0.87へ更新され、iOS向けにはCocoaPodsを使わないSwift Package Manager(SwiftPM)の実験的サポートが加わるなど、開発体験とビルド基盤の両面で大規模な刷新が行われた。今回のリリースには265件のコミットと74人の貢献者が関わっている。

## Strict TypeScript APIとその影響

Strict TypeScript APIは、React Nativeのソースコードから直接型定義を生成する仕組みで、内部のファイル構造が変わってもユーザー向けAPIの破壊的変更にはならない設計になっている。これに伴い、`react-native/Libraries/...`のようなdeep importは型エラーとなり、`import { TextInput } from 'react-native'`のようにルートエクスポートを使うことが必須になった。また`useRef<any>(null)`のような汎用的な型ではなく、`useRef<TextInputInstance>(null)`のようにコンポーネントごとの専用インスタンス型を使うよう変更されている。既存プロジェクトは0.88までの間、`tsconfig.json`に`customConditions`を設定することでレガシーなdeep importを許容するオプトアウトが可能だが、それ以降は強制される見込みだ。

## Metroの高速化とSwiftPM対応

MetroはこのリリースでバージョンOSSも0.84から0.87へ更新され、source map生成が2倍高速化、メモリ使用量も半減するなど、開発サーバーやReact Native DevToolsの読み込み体験が大きく改善された。`metro.config.mts`や`metro.config.cts`によるTypeScript/ESM設定にも対応した一方、`.es6`拡張子やYAML設定ファイルのサポートは廃止されている。iOS側では、`npx react-native spm --deintegrate`コマンドで既存の`.xcodeproj`にSwift Package Managerを統合できるようになった。CocoaPodsやRuby、Bundlerを必要とせず、依存関係の変更時には`pod install`なしで自動的にautolinkingが行われる。ただしコミュニティライブラリ側が`Package.swift`を提供している必要があり、未対応の場合は`npx react-native spm scaffold`でpodspecから生成する運用になる。ヘッダーのインポート方法も`#import <RCTAppDelegate.h>`から`#import <React/RCTAppDelegate.h>`へと名前空間付きの形式に変更された。

## 最小要件の引き上げとAPI削除

Android側ではAndroid Gradle Plugin(AGP) v9への対応が行われ、互換性維持のためには`android.builtInKotlin=false`と`android.newDsl=false`を`gradle.properties`に設定することが推奨されている(これらのフラグはAGP 10.xで削除予定)。あわせて最小要件がNode.js 22.13.0以上、Kotlin 2.0以上(バンドルは2.2.0)に引き上げられ、compileSdk/buildToolsも37へ、ライブラリが対象とすべき最小compileSdk(minCompileSdk)も34へと引き上げられた。非推奨機能の削除も進み、`InteractionManager.runAfterInteractions()`は`requestIdleCallback()`への置き換えが必要になったほか、`Modal`の`animated`プロパティ、`StatusBar.setBackgroundColor()`などのメソッド、`useTurboModules`フラグ(TurboModulesは常時有効化)、`useColorScheme()`が返していた`'unspecified'`値(nullに変更)などが削除されている。

## 今後の見通し

React Nativeチームは、deep importの自動修正やStrict TypeScript APIへの移行を支援するツールを用意しており、既存プロジェクトはReact Native Upgrade Helperを使った段階的なアップグレードが推奨されている。0.87が現行の最新版となり、0.84.x系のサポートは終了した。Expoユーザーは`expo@canary`リリースを通じて先行して利用可能となっている。今回のリリースは、型安全性の向上とビルドツールチェーンの近代化を同時に進めるものであり、今後のバージョンでもレガシーなdeep import許容の撤廃など、段階的な移行が続く見込みだ。
