---
date: "2026-04-07T10:38:41+09:00"
title: "TornadoVM 4.0 GA・Google ADK for Java 1.0など——2026年4月Javaエコシステム主要リリースまとめ"
description: "TornadoVM 4.0のApple Silicon対応GA、Google ADK for Java 1.0リリース、Java 26対応のIntelliJ IDEA 2026.1など、Javaエコシステムで主要アップデートが相次いだ。"
tags:
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/04/java-news-roundup-mar30-2026/"
  - "https://blog.jetbrains.com/idea/2026/04/java-annotated-monthly-april-2026/"
---

## 主要GAリリース：TornadoVM 4.0とGoogle ADK for Java 1.0

2026年4月初旬、Javaエコシステムで注目度の高いGA（正式版）リリースが2件相次いだ。

**TornadoVM 4.0.0**はGPUコンピューティングフレームワークの大型アップデートで、Apple Silicon向けの**Metal APIバックエンド**を新たにサポートした。これによりmacOSユーザーがAppleのGPUを活用したアクセラレーション計算を利用できるようになる。技術面ではPTXバックエンドへのSIMDシャッフル・リダクション intrinsicsの追加や、`TornadoExecutionPlan`クラスへの`withCUDAGraph()`メソッド追加（CUDAグラフ操作のキャプチャ用）も含まれる。JDK 25およびJDK 21の両方に対応している。

**Google Agent Development Kit（ADK）for Java 1.0.0**は、GoogleのオープンソースAIエージェントフレームワークが正式版に到達したリリースだ。`InMemoryArtifactService`クラスと`AgentExecutorProducer`の統合、ネイティブ非対応モデルでの`output_schema`と`tools`の同時使用サポートなどが含まれる。Javaエコシステムへのエージェント型AI統合を加速させる動きとして注目される。

## リリース候補・メンテナンスリリース

**Grails 7.1.0-RC1**では、Groovyの`invokedynamic`設定を`build.gradle`からGrails Gradle Pluginに移行する変更が盛り込まれ、設定の一元管理が改善された。また`@Service`アノテーションがドメインクラスのマッピングブロックからデータソースを自動継承するようになった。

**Gradle 9.5.0-RC1**はタスク失敗時の診断情報にprovenance情報を追加し、`DomainObjectCollection`インターフェースに`disallowChanges()`メソッドを導入してコレクションの変更を防止できるようにした。

メンテナンスリリースではApache Tomcat（11.0.21 / 10.1.54 / 9.0.117）がノンブロッキングフラッシュ問題の修正とHTTP/2エラーハンドリングの改善を提供。Apache Log4j 2.25.4もRFC5424Layoutの属性アライメント修正やXMLフォーマット・サニタイズ問題の修正を行った。

## Java 26・JDK 27とIntelliJ IDEA 2026.1

3月17日にリリースされた**Java 26**は現在のJavaエコシステムで最大のトピックとなっている。HTTP Clientのアップデート、セキュリティ・暗号化の強化、パフォーマンス改善が主な変更点だ。並行して**JDK 27**のEarly-Accessビルド16も公開されており、次世代への開発が着実に進んでいる。

JetBrainsは**IntelliJ IDEA 2026.1**をリリースし、Java 26への即日サポートを提供した。バーチャルスレッドデバッガーの改善、Kotlin 2.3.20サポート、Spring Dataおよびデバッガーの強化が含まれる。また、JavaScript/TypeScriptのコア機能の無料化も注目を集めた。JetBrainsのAIエージェントフレームワーク**Koog**がJavaサポートに拡張されたことも、Java×AIの文脈で重要な動きといえる。

## Jakarta EE 12の進捗とエコシステムの動向

**Jakarta EE 12**の開発では、Jakarta Connectors 3.0、Jakarta Faces 5.0、Jakarta Transactions 2.1、Jakarta JSON Processing 2.2などの仕様がMilestone 2に向けて開発中だ。セキュリティ仕様の統合やJakarta AuthorizationのWeb Profileへの組み込みについてコミュニティで議論が続いている。

イベント面では、3月にJavaOne 2026（Redwood Shores）が開催され、Anton Arhipov氏がIntelliJ IDEAの誕生25周年について講演を行った。同月にはIntelliJ IDEAドキュメンタリーも公開されている。4月には4月13〜15日のSpring I/O（バルセロナ）、4月22〜24日のDevoxx France（パリ）および4月23〜25日のDevoxx Greece（アテネ）など、Java関連の主要イベントが続く。
