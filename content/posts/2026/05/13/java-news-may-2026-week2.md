---
date: "2026-05-13T02:45:46+09:00"
title: "JDK 27向けJEP 533がターゲット昇格、Spring AI・Groovy・GrailsもM/Alphaリリース——Javaエコシステム週次動向"
description: "2026年5月第2週、JDK 27向けのJEP 533（Structured Concurrency）がTargeted状態に昇格し、Spring AI 2.0.0-M6・Groovy 6.0アルファ・Grails 8.0-M1など多数のJavaエコシステムプロジェクトが相次いでアップデートされた。"
tags:
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/05/java-news-roundup-may04-2026/"
---

## OpenJDK / JDK 27の動向

JDK 27に向けて、2つの重要なJEPがTargeted状態へ昇格した。**JEP 533（Structured Concurrency、第7プレビュー）**は、異なるスレッドで実行される関連タスクのグループを単一の作業単位として扱うことを目的とした機能で、引き続きプレビューを重ねながら安定性を高めている。**JEP 531（Lazy Constants、第3プレビュー）**もTargeted状態となり、今回の更新では`isInitialized()`と`orElse()`メソッドの削除、および新たなファクトリーメソッド`ofLazy()`の追加という変更が加わった。また、JDK 27のビルド21が各種コンポーネントのバグ修正とともにリリースされている。

## Spring AI 2.0.0-M6 と主要フレームワークのリリース

**Spring AI 2.0.0-M6**（第6マイルストーン）では、`ChatModel`インターフェースにベンダー非依存の動作を提供する新メソッド`buildRequestPrompt()`が追加された。また、`OpenAiEmbeddingOptions`内の`EncodingFormat`がこれまでの`String`型から`enum`型へと変更され、型安全性が向上している。

**Groovy 6.0.0-alpha**では、コレクション操作を拡張する`groupByMany()`メソッドと、メソッドの副作用を明示するための`@Modifies`アノテーションが新たに導入された。**Grails 8.0.0-M1**は非推奨コードの削除とCORSヘッダーの更新を主な変更点としており、フレームワークのモダナイゼーションが着実に進んでいる。ジョブスケジューリングライブラリ**JobRunr 8.6.0**はJEP 500でfinalフィールドのミューテーション制限が設けられたJDK 26への完全な互換性を実現し、大規模データベース環境での`getAllTableNames()`メソッドのパフォーマンス改善も含んでいる。

## Quarkusのセキュリティ修正とAI連携機能

**Quarkus**は今週、緊急メンテナンスリリースを公開した。**CVE-2026-39852**への対応が含まれており、この脆弱性は攻撃者がURLにセミコロンを付加することでセキュリティ制約を迂回できるというものだった。セキュリティ修正と同時に、新機能として**Quarkus Agent MCP**が導入された。これはModel Context Protocol（MCP）に対応したスタンドアロンサーバーで、AIエージェントがQuarkusアプリケーションの管理や拡張パターンへのアクセスを行えるようにするものだ。AIとJavaアプリケーション基盤の統合が進む動向を象徴するリリースとなっている。

## その他のアップデート

**GlassFish 8.0.2**はバグ修正、依存関係の更新、新機能2件、CVE解決2件を含むメンテナンスリリースとなった。**TomEE 10.1.5**および**Tomcat 11.0.22**も段階的な改善を伴うメンテナンスアップデートを公開している。**GraalVM**については、月次の機能リリーストレインを加速させるとともに、四半期ごとのCPU（Critical Patch Update）パッチの提供体制を整えており、より迅速なアップデートサイクルへの移行が進んでいる。
