---
date: "2026-09-01T08:10:51+09:00"
title: "Node.js 26.8.0リリース、暗号化APIにSIV/GCM-SIVモード追加とzlibのZIP対応が目玉に"
description: "Node.js 26.8.0が公開され、暗号化APIへのSIV/GCM-SIVモード追加、zlibモジュールへのZIPファイル操作クラス追加、REPLの構文ハイライト対応など多数の機能強化とセキュリティ修正が盛り込まれた。"
tags:
  - Programming Languages
references:
  - "https://nodejs.org/en/blog/release/v26.8.0"
---

## 概要

Node.jsプロジェクトは8月26日、26系（Current）の最新マイナーリリースとなるv26.8.0を公開した。リリースはAntoine du Hamel氏（@aduh95）によるもので、暗号化APIの拡張、zlibモジュールへのZIPファイル操作機能の追加、REPLの構文ハイライト対応など、開発者体験とセキュリティ両面での強化が多数盛り込まれている。

## 暗号化・SQLite関連の機能強化

目玉となるのがCipher/Decipher APIへのSIV（Synthetic Initialization Vector）およびGCM-SIVモードの追加だ（PR #63411）。これによりノンス誤用に強い認証付き暗号方式が利用可能になる。あわせてRSA-OAEP暗号化で`mgf1Hash`パラメータの指定に対応し、暗号方式選択の柔軟性が向上した。ルート証明書もNSS 3.126に更新されている。SQLiteモジュールでは`StatementSync.prototype.close()`と`Symbol.dispose`による明示的リソース管理（`using`構文）への対応が追加され（PR #64232）、準備済みステートメントのライフサイクル管理がしやすくなった。

## zlibのZIP対応とREPLの構文ハイライト

zlibモジュールには`ZipEntry`・`ZipFile`・`ZipBuffer`という新クラスが追加され、Node.js標準機能だけでZIPアーカイブの読み書きが可能になった（PR #64339）。中央ディレクトリレコード数の検証、あいまいなアーカイブ終端の拒否、ローカル/中央ヘッダー不一致の防止、FIFOやデバイスファイルの取り扱いなど、セキュリティ面の考慮も同時に組み込まれている。開発者向けにはREPLへの基本的な構文ハイライト機能が追加され（PR #64591）、対話的なコーディング時の可読性が向上した。このほか、例外を投げずにnullを返す非throwの`MIMEType.parse()`（PR #64965）や、`perf_hooks`のヒストグラムへの統計的仮説検定機能の追加（PR #65416）など、ユーティリティ・診断系APIの拡充も行われている。

## パフォーマンスとセキュリティ修正

パフォーマンス面では、WHATWG URLパーサーとURLSearchParamsの高速化、webstreamsのホットパスにおけるPromise生成の削減、HTTPサーバーでのインタラシブリストやヘッダーペアキャッシュの導入、`net.BlockList`の処理速度改善など幅広い最適化が行われた。再帰的な`readdir`では全エントリへの`stat`呼び出しを省略する最適化も加わっている。セキュリティ修正も多岐にわたり、FFI（外部関数インターフェース）でのSharedArrayBufferやデタッチ済みArrayBufferの不正な扱いを拒否する修正、文字列書き込みオフセットのオーバーフロー防止、`mkdtemp`や奇数長ucs2変換における境界外書き込みの修正、TLS/WebCryptoにおけるFIPSモード関連の修正などが含まれる。依存関係ではundiciが8.10.0に、libffiが3.8.0にそれぞれ更新された。なお`--enable-static`ビルドフラグは非推奨となり、今後は常時有効化される。
