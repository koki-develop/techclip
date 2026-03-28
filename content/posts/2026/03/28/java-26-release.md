---
date: "2026-03-28"
title: "Java 26正式リリース、HTTP/3対応やAOTキャッシュの全GC対応など10件のJEPを搭載"
description: "OracleがJava 26をGAリリースし、HTTP/3サポート、Lazy Constants、Structured Concurrencyなど10件のJEPによる言語革新・ライブラリ改善・パフォーマンス向上を提供した。"
tags:
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/03/java-news-roundup-mar16-2026/"
---

## 概要

Oracleは2026年3月17日、Java 26（JDK 26）を正式リリースした。JDK 25に続く非LTS（Long-Term Support）リリースとして、10件のJEP（Java Enhancement Proposal）が含まれている。そのうち5件はプレビューまたはインキュベーター段階の機能であり、残り5件が新規または確定済みの変更となる。近年のJavaリリースの中では比較的コンパクトなリリースだが、HTTP/3対応やGCの改善など実用的な機能強化が盛り込まれた。

## 搭載された10件のJEP

### 言語機能

- **JEP 500: Prepare to Make Final Mean Final** — `final`キーワードの意味をより厳密にするための準備。ディープリフレクションによるfinalフィールドの変更に対して警告が発せられるようになり、将来的には例外がスローされる予定。
- **JEP 525: Structured Concurrency（第6プレビュー）** — タスク階層とリソース管理を通じて、より明確で保守しやすい並行処理コードを記述できる構造化された並行性パターンの改良を継続。
- **JEP 530: Primitive Types in Patterns, instanceof, and switch（第4プレビュー）** — パターンマッチングをプリミティブ型に拡張し、条件分岐をより表現力豊かに記述可能にする。無条件の正確性の定義強化やswitch構文でのドミナンスチェックの厳格化が変更点。

### ライブラリ改善

- **JEP 517: HTTP/3 for the HTTP Client API** — 標準のHTTP Client APIにHTTP/3プロトコルのサポートを追加。最新のプロトコル標準を利用可能にする。
- **JEP 524: PEM Encodings of Cryptographic Objects（第2プレビュー）** — 暗号鍵、証明書、証明書失効リストをPEM形式でエンコードするAPIを提供。`PEMRecord`クラスが`PEM`にリネームされ、`KeyPair`や`PKCS8EncodedKeySpec`クラスの暗号化・復号化サポートが強化された。
- **JEP 526: Lazy Constants（第2プレビュー）** — 最大1回だけ初期化される不変の値ホルダーである「計算定数」を導入。finalフィールドのパフォーマンスと安全性の利点を持ちつつ、初期化タイミングの柔軟性を提供する。前回の「Stable Values」から名称が変更された。

### パフォーマンス向上

- **JEP 516: Ahead-of-Time Object Caching with Any GC** — JDK 24で提供されたJEP 483（Ahead-of-Time Class Loading & Linking）を拡張し、低レイテンシのZGCを含むすべてのガベージコレクタで起動時間とウォームアップ時間を改善。Project Leydenの一環。
- **JEP 522: G1 GC: Improve Throughput by Reducing Synchronization** — G1ガベージコレクタの同期オーバーヘッドを削減し、スループットを向上させる最適化。

### その他

- **JEP 529: Vector API（第11インキュベーター）** — ベクトル計算を最適なCPU命令にコンパイルするVector APIの11回目のインキュベーション。Project Valhallaの機能が利用可能になった時点でプレビューに移行予定。
- **JEP 504: Remove the Applet API** — JDK 9およびJDK 17で非推奨化されていたApplet APIを完全に削除。ブラウザアプレットの時代の終焉を反映した変更。

## 今後の展望

次期リリースのJDK 27は2026年9月のGAリリースが予定されている。現時点でターゲットされているJEPとして、JEP 527（Post-Quantum Hybrid Key Exchange for TLS 1.3）がある。また、Lazy Constantsの第3プレビューやProject Valhallaに基づくValue Classes and Objects（プレビュー）なども候補として挙がっている。BellSoftもLibericaJDK 26をリリースしており、OpenJDKからの2,665件を含む合計2,825件の修正が含まれるなど、Javaエコシステム全体がJDK 26への対応を進めている。
