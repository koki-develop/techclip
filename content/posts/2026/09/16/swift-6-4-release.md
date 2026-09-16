---
date: "2026-09-16T18:14:05+09:00"
title: "Swift 6.4がリリース、Swift Buildが標準ビルドシステムに ― WebAssembly連携も最大40倍高速化"
description: "Swift 6.4が公開され、SwiftPMのデフォルトビルドシステムがSwift Buildへ切り替わったほか、WebAssembly連携の大幅高速化や言語機能・相互運用性の改善が図られた。"
tags:
  - Programming Languages
references:
  - "https://www.swift.org/blog/swift-6.4-released/"
---

## 概要

Swift.orgは9月15日、プログラミング言語Swiftの最新版「Swift 6.4」をリリースした。アプリケーション開発だけでなく、サーバーサイド、システムプログラミング、組み込みデバイス、ブラウザ上のWebAssembly実行まで幅広い用途を見据えたアップデートで、ビルドシステムの刷新、言語機能の改善、他言語との相互運用性拡張、プラットフォーム対応の拡大など多岐にわたる変更が盛り込まれている。

## Swift Buildがデフォルトビルドシステムに

今回の目玉は、Swift Package Manager(SwiftPM)におけるデフォルトビルドシステムが新しい「Swift Build」へ切り替わったことだ。これにより、Linux・macOS・Windowsの各プラットフォームで一貫したビルド体験が得られるようになり、クロスプラットフォーム開発における環境差異の解消が進む。あわせて、SF-0007として提案されクロスプラットフォーム対応のプロセス実行を担う「Subprocess」ライブラリが、2025年の0.1版リリースを経て正式に1.0へ到達した。

## 言語機能とメモリ安全性の強化

言語仕様面では、オプショナル型を`some Rocket?`のように括弧なしで自然に記述できるようになったほか、コンパイラ警告を制御する`@diagnose`属性、名前衝突を解決するモジュールセレクタ(`::`)、defer ブロック内での非同期関数呼び出し対応、タスクのキャンセルから処理を保護する`withTaskCancellationShield`など、実用面の改善が多数加わった。パフォーマンスとメモリ安全性の分野では、非コピー可能な要素を保持しつつコピー・オン・ライトの恩恵をオーバーヘッドなしで受けられる新しいコレクション型が導入され、`UniqueArray`や`Iterable`プロトコル、`Ref`/`MutableRef`型といった仕組みによって安全性と効率性の両立が図られている。

## WebAssemblyと相互運用性の拡大

WebAssembly対応では、JavaScriptKitを介したWasm統合において、安全なブリッジング方式が従来の動的ブリッジングと比べて最大40倍高速化された。Wasm SDKはSwift.orgから直接入手できる。相互運用性の面でも、C++20の`std::span`とSwiftの`Span`が直接統合されたほか、Java・Kotlinとの非同期関数やコールバックへの対応が拡張され、C言語向けには`@implementation`サポートが強化されるなど、他言語エコシステムとの連携がさらに進んだ。

## 開発ツールとプラットフォーム対応

開発ツール面では、LLDBがモジュール依存関係をより正確に追跡できるようになりデバッグ体験が向上したほか、VS Code拡張がOpen VSX Registryでも配布されるようになった。またSPDXやCycloneDX形式に対応したSBOM生成機能も加わり、サプライチェーンの透明性確保をサポートする。プラットフォーム対応では、AndroidがNDK 30に対応しSwift Buildでの標準サポートが実現したほか、Embedded Swiftでは存在型やエラーハンドリングが強化され、WASI向けにはFileManagerの対応が改善された。今回の変更点はいずれもSwift Evolutionダッシュボードで確認でき、開発者はSwift Forumsを通じて今後の改善に引き続き貢献できる。
