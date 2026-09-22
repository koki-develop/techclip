---
date: "2026-09-23T08:10:45+09:00"
title: "Java 27正式リリース、G1 GCが全環境デフォルトに、耐量子暗号のTLS 1.3対応も追加"
description: "OracleがJava 27を正式リリースし、G1 GCの全環境デフォルト化や耐量子暗号のハイブリッド鍵交換など9つのJEPを導入した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://www.infoq.com/news/2026/09/java27-released/"
  - "https://www.publickey1.jp/blog/26/java_27g1_gctls_13.html"
---

## 概要

Oracleは9月16日、非LTS(Long-Term Support)版となる「Java 27」を正式リリースした。JDK 25以降では2回目の非LTSリリースにあたり、9件のJEP(JDK Enhancement Proposal)を収録している。目玉はガベージコレクタのG1 GCが全環境でデフォルトになったことと、TLS 1.3向けに耐量子暗号のハイブリッド鍵交換が追加されたことで、パフォーマンスとセキュリティの両面で将来を見据えた強化が図られている。なお非LTS版であるため、サポート期間は次期リリースであるJava 28が予定される2027年3月までの半年間に限られる。現行のLTS版はJava 25(2025年9月リリース)のままだ。

## パフォーマンス関連の強化

JEP 523「G1 GCを全環境でデフォルトに」では、これまでCPUコア数が1以下、あるいはメモリが2GB以下といった小規模環境ではSerial GCがデフォルトとして使われていたが、G1 GC自体の改善によって制約の大きいハードウェアでも同等の性能を発揮できるようになったため、全環境でG1 GCがデフォルトに統一された。あわせてJEP 534「Compact Object Headers」もデフォルト化に向けて前進しており、64ビット環境におけるオブジェクトヘッダーを96ビットから64ビットへ削減することで、ヒープの利用効率とデータの局所性を改善する。現時点ではコマンドラインでの明示的な有効化が必要とされている。またJEP 536「JFR In-Process Data Redaction」により、Java Flight Recorderが収集するデータのプロセス内での秘匿処理にも対応した。

## セキュリティ:耐量子暗号への対応

セキュリティ面での中心的な変更がJEP 527「Post-Quantum Hybrid Key Exchange for TLS 1.3」だ。これはIETFで策定中のハイブリッド鍵交換仕様を用いてRFC 8446(TLS 1.3)の実装を拡張するもので、既存コードを変更することなく耐量子暗号による鍵交換の恩恵を受けられる点が特徴となっている。Oracleは、標準化されたアルゴリズムを現行のLTS版にも展開し、「Javaエコシステム全体で耐量子暗号を広く利用可能にする」ことをロードマップとして掲げており、今回のJEP 527はその一環に位置づけられる。あわせてJEP 538「PEM Encodings of Cryptographic Objects」が3回目のプレビューを迎え、暗号鍵や証明書、証明書失効リストをPEM形式でエンコードするAPIの整備が進んでいる。

## 言語機能のプレビュー・インキュベータ

将来の言語進化に向けた実験的機能も複数プレビュー段階を重ねている。JEP 531「Lazy Constants」は3回目、JEP 532「Primitive Types in Patterns, instanceof, and switch」は5回目、JEP 533「Structured Concurrency」は7回目のプレビューとなり、JEP 537「Vector API」は12回目のインキュベータ段階に入った。これらの反復的な改善は、6か月ごとのリリースサイクルの中でイノベーションと企業利用における安定性のバランスを取るJavaの方針を反映したものだ。

## エコシステムとの連携・今後の見通し

Java Verified Portfolioにも新たな顔ぶれが加わった。OpenJDKのバージョニングにTip & Tailモデルで初めて足並みを揃えた「Helidon 27」、macOS向けにMetalレンダリングパイプラインやテキストコントロールの改善、アクセシビリティ強化を盛り込んだ「JavaFX 27」、そしてJDK 17・21・25・27への対応を拡張したFIPS 140-3準拠の暗号サービスプロバイダー「Oracle Jipher 20」が新たに加わっている。次期JDK 28(2027年3月予定)では6件のJEPが予定されており、Project Valhalla関連のJEP 539「Strict Field Initialization in the JVM」やJEP 401「Value Classes and Objects」のプレビュー入りが見込まれる。これによりVector APIもインキュベーションからプレビューへの昇格が視野に入るなど、Javaの長期的な言語進化が着実に進んでいることがうかがえる。
