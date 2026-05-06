---
date: "2026-05-07T02:38:05+09:00"
title: "Node.js 26正式リリース — Temporal APIがデフォルト有効化、V8 14.6への更新でモダン化が加速"
description: "Node.js 26.0.0がリリースされ、長年のDate APIの問題を解消するTemporal APIが標準で利用可能になるとともに、V8エンジン14.6への更新やレガシーコードの整理が行われた。"
tags:
  - Programming Languages
references:
  - "https://nodejs.org/en/blog/release/v26.0.0"
  - "https://linuxiac.com/node-js-26-debuts-with-temporal-api-enabled-by-default/"
---

## 概要

Node.js 26.0.0が2026年5月5日に正式リリースされた。本バージョンは「Current」ステータスで提供され、2026年10月にLTS（長期サポート）へ移行する予定だ。リリースマネージャーはRafael Gonzaga氏が担当している。最大のハイライトは、これまで実験的フラグ付きでのみ利用できたTemporal APIがデフォルトで有効化されたことだ。JavaScriptにおける日付・時刻処理の根本的な刷新が、ついて一般ユーザーの手に届く形となった。

## Temporal API — Dateの後継がついに標準化

Temporal APIは、従来の`Date`オブジェクトが抱えてきた多くの問題（タイムゾーン処理の曖昧さ、可変性、直感に反するAPI設計など）を解消するために開発されたモダンな日付・時刻APIだ。日付、時刻、期間、タイムゾーン、カレンダー対応操作のそれぞれに専用の型が用意されており、より安全で明確なコードが書けるよう設計されている。Node.js 26ではこのAPIがフラグなしで利用できるようになったことで、実プロジェクトへの採用が現実的なものとなった。

## V8 14.6とJavaScript新機能

V8エンジンがChromium 146ベースの14.6.202.33に更新された。これに伴い、いくつかの新しいJavaScript言語機能が利用可能になった。`Map.prototype.getOrInsert()`および`Map.prototype.getOrInsertComputed()`（`WeakMap`版も含む）は、キーが存在しない場合に値を挿入する操作を簡潔に書けるUpsertパターンのサポートだ。また`Iterator.concat()`によるイテレーターの連結も追加されている。なお、`NODE_MODULE_VERSION`は147に更新されており、ネイティブアドオンの再コンパイルが必要になる場合がある。

## レガシー機能の削除と非推奨化

Node.js 26ではプラットフォームのモダン化を意図した整理も行われた。`http.Server.prototype.writeHeader()`メソッドが削除され、代わりに`writeHead()`の使用が求められる。内部ストリームモジュール群（`_stream_wrap`、`_stream_readable`、`_stream_writable`など）も廃止された。また`module.register()`やストリーム・暗号関連のAPIがランタイム非推奨（DEP0201、DEP0203、DEP0204）に昇格した。HTTPクライアントライブラリUndiciは8.0.2へ更新されている。セキュリティ面ではCVE-2026-21717（配列インデックスハッシュ衝突）への対応が含まれる。

## ビルド要件の変更

ビルド環境の要件も引き上げられた。GCC 13.2以上が必須となり、Python 3.9のサポートが廃止された。Windows向けにはSDKバージョン11への更新が必要となる。これらの変更は、古いビルド環境で独自にNode.jsをコンパイルしているケースに影響する。Node.js 26はLTSへの移行を控えた重要なバージョンであり、新機能の評価と既存アプリケーションへの影響確認を今のうちに進めておくことが推奨される。
