---
date: "2026-10-17T18:12:03+09:00"
title: "Node.js v26.12.0とv24.22.0が公開、WebSocketマスク処理APIやSQLiteの安全性強化を追加"
description: "Node.jsプロジェクトがCurrent系列のv26.12.0とLTS系列のv24.22.0を公開し、WebSocket向け新APIやSQLiteの堅牢性向上などを盛り込んだ。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://nodejs.org/en/blog/release/v26.12.0"
  - "https://nodejs.org/en/blog/release/v24.22.0"
---

## 概要

Node.jsプロジェクトは10月14日、Current系列の最新版v26.12.0と、LTS系列（コードネームKrypton）の最新版v24.22.0を公開した。いずれもマイナーアップデートだが、WebSocket通信やSQLiteモジュールの安全性・堅牢性を高める変更が多数取り込まれており、今後年1回のメジャーリリースサイクルへ移行するというリリーススケジュール変更を控えた節目のアップデートと位置づけられる。

## WebSocketとAPIまわりの拡張

v26.12.0ではhttpモジュールに`websocketMask()`と`websocketUnmask()`が新たに追加された。これによりWebSocketフレームのマスキング／アンマスキング処理をアプリケーション側から直接制御できるようになり、WebSocketサーバーやプロキシの実装者にとって低レベルの処理を自前で組み立てやすくなる。また、WebAssemblyまたは正規表現（RegExp）サポートが欠けた環境ではエラーをスローするよう変更され、実行環境間での挙動の一貫性が向上した。

一方のv24.22.0ではcrypto関連の拡張が目立つ。PKCS#12形式を解析する`crypto.parsePKCS12()`、汎用メッセージ認証コードを扱うGeneric MAC API、SIV/GCM-SIVモードのCipher/Decipher対応などが加わったほか、OpenSSLプロバイダーから利用可能な暗号・ハッシュアルゴリズムを動的に検出できるようになった。このほかパフォーマンス計測用のperformance hooksに`SlidingWindowHistogram`や信頼区間を算出する`meanCI`、ヒストグラムのCBORエクスポート／インポートが加わり、ユーティリティ関数には`util.debounce()`や`util.throttle()`が新設されるなど、アプリケーション開発者向けの地味だが実用的な機能追加が多い。

## SQLiteモジュールの安全性強化

両バージョンに共通するテーマの一つがSQLiteモジュールの堅牢化だ。v26.12.0では、サイズ超過の文字列を扱った際にプロセスを中止（abort）するのではなくエラー（ERR_STRING_TOO_LONG）をスローするよう変更され、予測可能なエラーハンドリングが可能になった。また`enableDefensive()`で有効化した防御的モードの設定がデータベースの再オープン後も保持されるようになったほか、集約関数（aggregate）の名前やオプションの検証も強化され、不正な値の使用を防ぐ。v24.22.0側でも`StatementSync.prototype.close()`と`Symbol.dispose`によるdispose protocol対応が加わり、ステートメントのリソース管理がしやすくなっている。

## その他の改善と依存関係の更新

v26.12.0ではStream/Iterator関連の改善として`dump()`/`dumpSync()`が追加されたほか、閉じたストリームへの書き込みでTypeErrorをスローするようエラーハンドリングが強化された。また不要なミューテックスやロック機構を削除することでcrypto処理のパフォーマンスが向上している。依存関係ではacornが8.19.0、sqliteが3.54.0、simdjsonが5.0.3にそれぞれ更新された。

v24.22.0ではHTTP/HTTP2のソケット破棄やチャンク書き込みの最適化、TLSのSNICallback・OCSPRequestまわりの改善、Windows環境での読み取り専用ファイル削除対応など、幅広い修正が入っている。セキュリティ面ではFIPSモードの改善とFIPS indicator diagnostics channelの追加、WebCryptoでの非FIPSパスの無効化が行われた。依存関係はnpmが11.19.1、simdjsonが4.6.11、zlibが1.3.2.1-motleyに更新されている。

今回のリリースは単体の目玉機能よりも、WebSocketやSQLiteまわりの安全性・一貫性を底上げする地道な改善が中心であり、Node.jsが年1回のメジャーリリースサイクルへ移行する前段階として、既存機能の安定性を固める意図がうかがえる。
