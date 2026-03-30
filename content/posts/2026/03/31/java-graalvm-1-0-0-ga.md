---
date: "2026-03-31"
title: "GraalVM Native Build Tools 1.0.0 GA、EclipseLink 5.0.0など、Javaエコシステムで相次ぐ主要リリース"
description: "GraalVM Native Build Tools 1.0.0のGA版をはじめ、EclipseLink 5.0.0やSpring Boot 4.1.0 M4など、Javaエコシステムの複数のフレームワークが同週にリリースされた。"
tags:
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/03/java-news-roundup-mar23-2026/"
---

## 概要

2026年3月最終週、Javaエコシステムにおいて複数の重要なリリースが相次いだ。最大のトピックはGraalVM Native Build Tools 1.0.0のGA（一般提供）達成であり、依存ライブラリのアップグレードと、最新GraalVM JDK上でGradleプラグインのテストが通らなくなる重大な問題の修正が盛り込まれた。Jakarta EE 11対応のEclipseLink 5.0.0 GAも同時期に登場し、JakartaエコシステムとJava標準仕様の進化が着実に進んでいることを示している。

JDK 27については早期アクセスビルド15が公開され、前ビルドからのバグ修正と改善が加えられた。また、Jakarta EE 11実装の参照実装であるGlassFish 8.0.1が初のメンテナンスリリースとして提供され、Java Native Accessライブラリの専用モジュールへの移動やデプロイパフォーマンスの最適化などが行われた。

## 主要リリースの詳細

**GraalVM Native Build Tools 1.0.0 GA**はメジャーバージョン1.0として初めてGAに到達したリリースで、GradleプラグインのJavaApplicationFunctionalTestクラスが最新GraalVM JDKで動作しなくなっていた問題（削除された機能に起因）が解消された。ネイティブコンパイルワークフローの安定性が高まり、本番利用に適した品質水準に達したことを意味する。

**EclipseLink 5.0.0 GA**はJakarta Persistence 3.2仕様をサポートし、Jakarta EE 11のエコシステムに正式対応した。JPQL強化やクエリ処理の改善、Oracle・MySQL・DB2・PostgreSQLを含む各種データベースプラットフォームの改善が含まれる。

Springエコシステムでは3つのマイルストーンリリースが提供された。**Spring Boot 4.1.0 M4**はgRPCサーバー・クライアント観測設定の一貫性を確保し、Micrometer Metricsのカスタムコンベンション対応を追加。**Spring Modulith 2.1.0 M4**はJobRunrイベント外部化サポートを導入。**Spring AI 2.0.0 M4**はGemini 3モデル向けのカスタムツール設定とネイティブ構造化出力の動的無効化をサポートした。

## クラウドネイティブとマイクロサービス関連

**Open Liberty 26.0.0.3 GA**では、`UserRegistry`インターフェースに属性ベースのユーザー取得を行う新メソッド`getUsersByAttribute()`が追加され、起動最適化のために最新Jandexインデックス形式がサポートされた。**Quarkus 3.34.0**では`ObjectLoader`インターフェースが内部専用として非推奨化され、`PathTree`インターフェースにリソース名取得メソッド`getResourceNames()`が新設された。

分散キャッシュの**Infinispan**は16.2.0の最初の開発版を公開し、Redisシリアル化プロトコルで`BITFIELD`・`SUBSCRIBE`・`PUNSUBSCRIBE`・`DIGEST`コマンドを拡張、REST APIへのOpenAPI v3仕様実装も行われた。

## 今後の見通し

今回のリリース群はネイティブコンパイル、クラウドネイティブ対応、Jakarta EE 11準拠という3つの軸でJavaプラットフォームが積極的に進化していることを示している。GraalVM Native Build Tools 1.0.0のGA到達は、Javaアプリケーションのネイティブイメージ化がより安定した開発体験を提供できる段階に入ったことを意味する。Spring BootやQuarkus、Open Libertyが同週にリリースを揃えたことは、Javaエコシステム全体が連動して前進している様子を映し出している。
