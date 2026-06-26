---
date: "2026-06-27T02:38:33+09:00"
title: "Node.js 26.4.0リリース：仮想ファイルシステムサポートやパッケージマップなど多数の新機能追加"
description: "Node.js 26.4.0（Current）がリリースされ、仮想ファイルシステム（VFS）の最小実装、パッケージマップによるモジュール解決、TLS証明書圧縮など多数の新機能とパフォーマンス改善が加わった。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://nodejs.org/en/blog/release/v26.4.0"
---

## 概要

Node.jsチームは2026年6月24日、Current版の最新リリースとなる**Node.js 26.4.0**を公開した。リリース担当はAntoine du Hamel（@aduh95）氏。本バージョンでは、仮想ファイルシステム（VFS）サブシステムの最小実装、パッケージマップを用いたモジュール解決、TLS証明書圧縮オプションなど、開発者の利便性とシステムの柔軟性を高める機能が複数追加された。

## 主要な新機能

### 仮想ファイルシステム（node:vfs）

最も注目すべき新機能は、`node:vfs` モジュールとして提供される**仮想ファイルシステム（VFS）サブシステム**の最小実装だ。これにより `node:fs/promises` のAPI呼び出しをマウントされたVFSインスタンスへディスパッチできるようになり、テストや組み込みシナリオでファイルシステムを仮想化する際の基盤となる。

### パッケージマップによるモジュール解決

ローダーに**パッケージマップ（Package Maps）**機能が追加された（Maël Nison氏の貢献）。これはモジュール識別子の解決をカスタマイズする仕組みで、モジュールのエイリアスやリマップが柔軟に行えるようになる。大規模なモノレポ構成やカスタムモジュールロード戦略を採用しているプロジェクトに特に有用だ。

### TLS証明書圧縮

Tim Perry氏が実装した `certificateCompression` オプションにより、TLSハンドシェイク時の証明書データを圧縮できるようになった。証明書サイズの削減によりネットワーク帯域幅の節約と接続確立の高速化が期待される。

### その他の注目機能

- **FS改善**: `readFile()` でユーザー提供のバッファを使用できるようになり、メモリ効率が向上（Matteo Collina氏）
- **HTTP改善**: `closeIdleConnections()` がpre-requestソケットもクローズするよう改善され、接続管理が最適化
- **NET強化**: `setKeepAlive()` が `TCP_KEEPINTVL` と `TCP_KEEPCNT` をサポートし、TCPキープアライブの詳細な制御が可能に（Guy Bedford氏）
- **dgram**: `bindSync()` と `connectSync()` という同期メソッドが追加された
- **FFI**: AArch64およびx86_64向けの実験的な高速FFI呼び出しAPIが実装され、ほぼ全プラットフォームでのサポートも追加

## パフォーマンス改善とバグ修正

パフォーマンス面では複数の最適化が施された。`Buffer.prototype.copy()` の高速化、simdutfを活用したUTF-8バイト長計算の高速化、WHATWGストリームのホットパスにおけるメモリ割り当ての削減、`addAbortListener` のオプションキャッシングによる高速化などが含まれる。

セキュリティ面では、CryptoモジュールにおけるHash._transformの未処理エラーの修正、`BN_get_word` エラーを無視しない修正（Crypto/TLS）、SQLiteのスタック使用後スコープバグの修正が行われた。バグ修正としては、WindowsでEPERMエラーをENOTEMPTYエラーとして誤扱いしない修正、`URLSearchParams(null)` が `null=` を正しく生成するよう修正なども含まれる。

## 依存関係の更新

依存ライブラリも複数アップデートされた。主なものとして npm 11.17.0、SQLite 3.53.2、libffi 3.6.0、acorn 8.17.0、ngtcp2 1.23.0、nghttp3 1.16.0が更新された。また `blockList` APIの安定性ステータスがリリース候補（Release Candidate）に引き上げられ、正式安定化に向けて一歩前進した。
