---
date: "2026-04-14T10:37:57+09:00"
title: "JDK 27が2026年9月14日GA予定、Java週次まとめ：HibernateやLangChain4j新版も登場"
description: "JDK 27のリリーススケジュールが正式提案され、GAは2026年9月14日に設定されたほか、Hibernate ORM 7.3.0やLangChain4j 1.13.0など主要フレームワークの新版リリースも相次いだ。"
tags:
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/04/java-news-roundup-apr06-2026/"
---

## JDK 27リリーススケジュールの提案

Mark ReinholdがJDK 27のリリーススケジュールを提案し、2026年6月4日にRampdown Phase Oneへ移行、**2026年9月14日に一般提供（GA）** を予定している。このスケジュールのレビュー期間は2026年4月13日に終了した。言語機能面では、JEP 532「パターン、instanceof、switch におけるプリミティブ型」が第5プレビューステータスに到達し、JDK 23〜26における以前のイテレーションから変更なく継続されている。

## フレームワークの新版リリース

**Hibernate ORM 7.3.0** では新たに `KeyType` 列挙型と `@NaturalIdClass` アノテーションが導入され、従来の識別子ベースのアプローチに加えて、ナチュラルIDを用いたエンティティのロードが可能となった。

**LangChain4j 1.13.0** では `RecoverabilityIT` と `PendingResponse` クラスによる永続化可能な実行状態が追加されたほか、HQLクエリのための `HibernateContentRetriever` も利用できるようになった。AIワークフローの信頼性向上に向けた機能強化が進んでいる。

**Keycloak 26.6.0** はRFC 7523によるJWT認証を実装し、OAuth Client ID Metadata Documentを通じたModel Context Protocol（MCP）のサポートを実験的機能として追加した。**Helidon 4.4.1** はSmile Data Format（バイナリJSONフォーマット）を実装し、設定における遅延環境変数トラバーサルを復元している。

## セキュリティと開発者ツール

Spring Cloud GatewayでCVEが開示された。**CVE-2026-22750** は `spring.ssl.bundle` の設定が静かに無視されるという脆弱性で、開発者がSSL設定を有効と誤認するリスクがある。SSL/TLSを利用しているアプリケーションでは影響範囲の確認が推奨される。

開発ツールの面ではJetBrainsが **Junie CLI** をIDEに統合し、IDEの自動検出とプロジェクトコンテキストの認識機能を持つコーディングエージェントが利用可能となった。また、Google ADK for Java 1.1.0 ではチャット補完モデルとGemmaのサポートが追加されている。
