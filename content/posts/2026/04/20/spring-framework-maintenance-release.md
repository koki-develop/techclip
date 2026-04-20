---
date: "2026-04-20T10:38:40+09:00"
title: "Spring Framework 6.2.18と7.0.7がリリース——バグ修正と機能改善を多数含むメンテナンスアップデート"
description: "Spring Framework 6.2.18（27件の修正）と7.0.7（52件の修正）がリリースされ、バリデーターのパフォーマンス向上やKotlinサポート改善など多数のバグ修正が加えられた。"
tags:
  - Programming Languages
references:
  - "https://spring.io/blog/2026/04/17/spring-framework-6-2-18-and-7-0-7-available-now/"
  - "https://github.com/spring-projects/spring-framework/releases/tag/v6.2.18"
  - "https://github.com/spring-projects/spring-framework/releases/tag/v7.0.7"
---

## 概要

Spring Frameworkは2026年4月17日、6.2.18と7.0.7の2バージョンを同時リリースした。どちらもバグ修正とドキュメント改善を主体とするメンテナンスリリースで、6.2.18では27件、7.0.7では52件の修正が含まれる。6.2.18は近日リリース予定のSpring Boot 3.5.14にも同梱される予定となっており、既存の本番環境での安定稼働を重視するプロジェクトにとって重要なアップデートだ。

## Spring Framework 6.2.18の主な変更点

6.2.18では、`SpringValidatorAdapter`と`MethodValidationAdapter`のパフォーマンス向上が図られた。また、将来のバージョン7.0で削除予定の機能に`@Deprecated(forRemoval = true)`アノテーションが追加され、移行準備を進める開発者への明示的なシグナルが強化されている。

バグ修正面では、`ServerSentEvent`のidやeventプロパティ設定時に発生していたNullPointerExceptionの解消、`@Sql`アノテーションと`TransactionAwareDataSourceProxy`を組み合わせた際の不具合修正、`WebDataBinder`が不要なコレクションを生成する問題の解決などが行われた。また、MySQLのGalera/WSREPコンフリクト（エラーコード149）への対応やKotlinのnullableな値クラスパラメータの処理改善も含まれている。依存ライブラリはMicrometer 1.15.11とReactor 2024.0.17にアップグレードされた。

## Spring Framework 7.0.7の主な変更点

7.0.7はより多くの修正を含む。6.2.18と共通する`SpringValidatorAdapter`や`MethodValidationAdapter`のパフォーマンス改善に加え、`KotlinSerializationJsonDecoder`でのJSON配列から`Flux`へのデコーディング対応、`RestClient`向けの`MockRestServiceServer#createServer`バリアント追加、`RestTemplateXhrTransport`を置き換える`RestClientXhrTransport`の新設など、新機能も盛り込まれている。

バグ修正では、`WebDataBinder`が「!」や「_」プレフィックス使用時に不要なコレクションを生成する問題、`MessageSourceSupport`における高カーディナリティのキャッシュ汚染問題、Java 24以降での`AnnotatedTypeMetadata`のソース宣言順序保持に関する問題、`MergedAnnotation.asMap()`が存在しないクラスを参照した際の失敗など、より高度な環境での動作安定性が強化された。依存ライブラリはMicrometer 1.16.5とReactor 2025.0.5にアップグレードされている。

## ドキュメント改善と今後の展望

両バージョンともSpEL式のホワイトスペース仕様の明確化、`@ActiveProfiles`の動作解説、Bean OverridesのKotlinサンプルコード追加など、ドキュメントの充実が図られた。6.2.x系は引き続きメンテナンスブランチとして維持され、7.0.x系は最新安定版として機能追加も継続して行われる。Spring Boot利用者は、近日公開予定の3.5.14を通じて6.2.18の修正を自動的に受け取ることができる。
