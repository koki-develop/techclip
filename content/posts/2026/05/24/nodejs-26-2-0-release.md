---
date: "2026-05-24T02:26:57+09:00"
title: "Node.js 26.2.0リリース — Temporal API統合、量子耐性暗号、HTTP 1xx新メソッドを追加"
description: "Node.js 26.2.0がリリースされ、ファイルシステム統計へのTemporal.Instantサポート、BoringSSL向け量子耐性暗号（ML-DSA・ML-KEM）、HTTPの新メソッド`writeInformation()`など100件以上の改善が加わった。"
tags:
  - Programming Languages
references:
  - "https://nodejs.org/en/blog/release/v26.2.0"
---

## 概要

Node.jsチームは2026年5月20日、Current系の最新版となる**Node.js 26.2.0**をリリースした。リリースマネージャーは@aduh95が務め、100件以上のコミットが含まれる大型アップデートとなっている。今回の目玉は、JavaScriptのTemporal APIをファイルシステム統計オブジェクトへ組み込んだことに加え、次世代の量子耐性暗号アルゴリズムのサポート開始、そしてHTTPプロトコルに関する利便性向上である。

## Temporal APIとファイル統計の統合

セマバー的にMINORの追加として、`fs.Stats`および`fs.BigIntStats`オブジェクトに`Temporal.Instant`サポートが実装された（PR #60789）。従来のDateオブジェクトはタイムゾーン処理や算術演算において多くの落とし穴があったが、Temporal APIを活用することでより精確かつ安全な日時操作が可能になる。合わせてStatsオブジェクト上のDateプロパティがenumerableに変更され（PR #63328）、オブジェクトの列挙やシリアライズ時の挙動が改善された。

## 量子耐性暗号のサポート

BoringSSL環境向けに**ML-DSA**（Module-Lattice-Based Digital Signature Algorithm）と**ML-KEM**（Module-Lattice-Based Key-Encapsulation Mechanism）の2つの量子耐性暗号アルゴリズムが追加された。これらはNIST（米国標準技術研究所）が標準化を進めているポスト量子暗号の代表格であり、将来の量子コンピュータによる攻撃に備えたアプリケーション開発が可能となる。暗号関連では他にも、Web Cryptography APIでの**ChaCha20-Poly1305**と**AES-KW**のサポート追加、CryptoKeyとKeyObjectの内部スロットセキュリティ強化、macOSでのシステム証明書列挙改善なども含まれている。

## HTTP 1xxステータスコードとその他の新機能

HTTPモジュールに新メソッド`writeInformation()`が追加され（PR #63155）、任意の1xxステータスコードを応答として送信できるようになった。これにより、`103 Early Hints`などのプリロードヒントや進捗通知など、中間的なHTTPレスポンスを扱う実装が容易になる。また長らく実験的扱いだった`stream.compose`がstableとして昇格したほか、QUICプロトコルの内部実装が完全に整備され`--allow-net`パーミッションへの対応も加わった。テストランナーでもタグによるフィルタリング機能が追加され、大規模なテストスイートの管理が改善された。

## 依存関係の更新

主要な依存パッケージも更新されており、`undici`が8.3.0、`corepack`が0.35.0、`sqlite`が3.53.1、`simdjson`が4.6.4、QUICライブラリの`ngtcp2`が1.22.1へそれぞれバージョンアップしている。Node.js 26.2.0のバイナリおよびソースコードは[公式サイト](https://nodejs.org/dist/v26.2.0/)からダウンロード可能だ。
