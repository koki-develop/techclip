---
date: "2026-06-15T02:33:59+09:00"
title: "JDK 27がランプダウンフェーズ1へ移行、JDK 28エキスパートグループも始動"
description: "JDK 27が安定化フェーズに入りJEPの追加が締め切られたほか、JDK 28の専門家グループ設立が承認され、Java開発の次世代ロードマップが明確化された。"
tags:
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/06/java-news-roundup-jun01-2026/"
---

## JDK 27、ランプダウンフェーズ1に到達

JDK 27が正式にランプダウンフェーズ1へ移行し、メインリポジトリからの安定化リポジトリへのフォークが完了した。これによりJEP（JDK Enhancement Proposal）の追加が締め切られ、GA（一般提供）リリースに向けた最終的な安定化作業が本格化する。2026年3月のGAリリースに向けて確定した機能は9つで、ガベージコレクションの改善、暗号化機能の強化、構造化並行処理（Structured Concurrency）関連の機能が含まれている。

注目すべき変更として、JEP 538「暗号オブジェクトのPEMエンコーディング」が3度目のプレビューを迎え、PEMレコードクラスの再分類や`DEREncodable`インターフェースの`BinaryEncodable`への改名など、APIの明確化に向けた改訂が加えられた。

## JDK 28エキスパートグループの発足

JSR 403の承認により、JDK 28の仕様策定を担う4名構成のエキスパートグループが設立された。仕様リードはOracleのIris Clarkが務め、Azul SystemsのSimon Ritter、Eclipse FoundationのStephan Herrmann、SAP SEのChristoph Langerが参加する。パブリックレビュー期間は2026年12月から2027年2月を予定しており、GAリリースは2027年3月を目標としている。

## Javaエコシステムの各種アップデート

エンタープライズ向けの動きとして、**GlassFish 8.0.3**がリリースされた。Jakarta Facesのレンダリングが従来比2倍に高速化されるほか、Embedded GlassFishの起動時間短縮も実現した。また、セキュリティ脆弱性CVE-2024-9342への対応も含まれている。OmniFishの**Arquillian Connector Suite 2.2.0**では、起動済みのGlassFishインスタンスプールを共有する仕組みにより、Jakarta EE TCKテストの実行時間を数時間から数分へと大幅に削減した。

その他のリリースとして、**Infinispan 16.2.0**が新たな確率的データ構造を加えたRedisプロトコルサポートの拡張を提供。**Kotlin 2.4.0**ではJDK 26のサポート、インクリメンタルコンパイルのデフォルト有効化、WebAssembly Component Modelへの対応が追加された。**Micronaut 5.0.1/5.0.2**はリダイレクト脆弱性やヘッダー転送リスクに対処するセキュリティパッチを適用している。
