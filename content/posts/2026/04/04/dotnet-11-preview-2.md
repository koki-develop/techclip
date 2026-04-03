---
date: "2026-04-04T02:16:45+09:00"
title: ".NET 11 Preview 2リリース：ネイティブOpenTelemetry対応、C# 15 Union Types、Aspire 13.2の大型アップデート"
description: ".NET 11 Preview 2がリリースされ、ASP.NET Coreへのネイティブ OpenTelemetryサポートやKestrelの最大40%スループット改善、C# 15のUnion Types、EF Core 11の新API、Aspire 13.2の大規模更新など多数の強化が盛り込まれた。"
tags:
  - Programming Languages
references:
  - "https://gingter.org/2026/04/01/dotnet-news-march-2026/"
---

## 概要

2026年3月、.NETエコシステムはメジャーリリースサイクル外にもかかわらず非常に活発な動きを見せた。中心となるのは**.NET 11 Preview 2**のリリースで、ランタイムの非同期処理改善、ASP.NET Coreへのネイティブ OpenTelemetryサポート、Kestrelの大幅なスループット向上など多岐にわたる機能強化が含まれている。加えて、C# 15の注目機能であるUnion Types、Entity Framework Core 11の進捗、Aspire 13.2のリリースもこの月のハイライトとなった。

## ランタイムとASP.NET Coreの強化

Preview 2では**Runtime Async**機能の開発が継続されており、非同期処理の仕組みをコンパイラが生成するステートマシンからランタイム側へ移行することで、スタックトレースの改善とオーバーヘッドの削減が実現される。JITの改善としては、境界チェックの除去、冗長なcheckedコンテキストの削除、新しいArm SVE2 intrinsics、キャッシュされたインターフェースディスパッチなどが追加された。

ASP.NET Coreでは、別途計装ライブラリを必要とせず`Microsoft.AspNetCore`アクティビティソースを直接購読できる**ネイティブ OpenTelemetryトレーシング**が導入された。Kestrelでは不正なHTTPリクエストを例外なしで処理するコードパスが追加され、該当シナリオで**最大20〜40%のスループット改善**が報告されている。Blazor SSRではTempDataサポートによりPOST-Redirect-GETパターンが利用可能になり、WebAssembly向けの.NET Web Workerプロジェクトテンプレートも追加された。

## C# 15 Union Typesと言語機能

C# 15の目玉機能として注目を集める**Union Types**は、`public union Pet(Cat, Dog, Bird);`という簡潔な構文で1-of-Nの値を型安全に表現できる。各ケース型からの暗黙の変換、コンパイラによる網羅的なswitchの強制など、従来のDiscriminated Unionsパターンを言語レベルでサポートする。コンパイラがケースの見落としを防ぐため、構文的な便利機能にとどまらず本番環境で実用できる堅牢な機能として設計されている。

## EF Core 11、Aspire 13.2、その他のアップデート

**EF Core 11**では`MaxByAsync`と`MinByAsync`が直接SQLに変換されるようになり、従来の`OrderByDescending(...).First()`といった回避策が不要になった。SQL ServerでのDiskANNベクターインデックスと`VECTOR_SEARCH()`サポートも追加され、専用のベクターデータベースなしに既存のSQL Server上でセマンティック検索やRAG型検索が実現できる。

**Aspire 13.2**はAspire Confで公開され、1,100件以上のIssueをクローズする大規模アップデートとなった。AIコーディングエージェントを意識した設計が取り入れられており、`aspire start`や`aspire stop`など充実したCLIコマンドでエージェントによる環境管理が可能になった。TypeScript AppHostの追加により、.NET SDKを必要とせずTypeScriptだけでAspireのオーケストレーションが行えるようになった点も注目される。また、**Rider 2026.1**安定版はASM Viewer、ファイルベースのC#プログラム実行、混合モードデバッグ、C# 15の早期サポートなどを提供している。

## 今後の展望

Runtime Asyncや Union Typesといった大型機能はまだプレビュー段階にあり、.NET 11の正式リリースに向けてさらなる改良が続く見込みだ。3月には緊急パッチ（.NET 10.0.5）がわずか2日で対応された事例もあり、チームの迅速な対応力も改めて示された。開発者コミュニティにとっては、C# 15の型システム強化と観測可能性（OpenTelemetry）の標準化が特に実用面での恩恵をもたらしそうだ。
