---
date: "2026-10-31T08:07:33+09:00"
title: "Node.js 26「Lithium」がLTS入り、Temporal API標準搭載のまま2029年まで長期サポートへ"
description: "Node.js 26系が長期サポート版「Lithium」に移行し、Temporal APIのデフォルト有効化やV8 14.6・Undici 8などを含んだ状態で2029年4月まで安定運用できる段階に入った。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://nodejs.org/en/blog/release/v26.13.0"
  - "https://nodejs.org/en/blog/release/v26.0.0"
  - "https://nodesource.com/blog/nodejs-v26-is-here"
---

## 概要

Node.js 26系が10月28日、バージョン26.13.0のリリースをもって長期サポート(LTS)版「Lithium」へ正式に移行した。サポート期間は2029年4月末までで、`process.release` のメタデータもLTSを反映する内容に更新されている。26.12.1からの機能的な変更はなく、今回のリリースは5月の26.0.0登場以来約半年間「Current」として検証されてきた内容を、そのまま本番環境向けの安定版として確定させるものだ。

## Temporal APIのデフォルト有効化とV8・Undiciの更新

今回のLTS移行で最も注目されるのは、JavaScriptの新しい日時API「Temporal」がフラグなしでデフォルト有効化された状態のままLTSに持ち込まれたことだ。Temporalは従来の`Date`オブジェクトが抱えていたタイムゾーン処理の曖昧さや可変性の問題を解消するために設計され、不変(immutable)な日時オブジェクトと明示的なタイムゾーン処理を提供する。長年の課題だったJavaScriptの日時操作の扱いにくさに対する本格的な解決策として、エコシステム全体への影響が大きい変更といえる。

JavaScriptエンジンはChromium 146相当のV8 14.6.202.33に更新され、`[Weak]Map.prototype.getOrInsert()`や`Iterator.concat()`といった新しいプロポーザルが利用可能になった。また、グローバルな`fetch()`実装やHTTP/1.1・HTTP/2通信を担うHTTPクライアント層であるUndiciもバージョン8.0.2へ更新され、WHATWG Fetch仕様への準拠強化とストリーミング・接続管理の信頼性向上が図られている。

## 非推奨APIの削除とアップグレード時の注意点

26.0.0ではSEMVER-MAJORの変更として、`http.writeHeader()`の完全削除(`http.writeHead()`への移行が必要)や、`_stream_wrap`・`_stream_readable`などレガシーなStreamモジュール群の削除、`--experimental-transform-types`フラグの廃止といった整理が行われている。ビルド要件もGCC 13.2以上への引き上げやPython 3.9サポートの終了など、開発環境側の対応が必要になる変更が含まれる。

さらに実運用上の注意点として、Node.js 25以降のLinux公式バイナリは`libatomic`にリンクされるようになっており、Node.js 22や24など以前のLTSから移行する場合、ディストリビューションによっては`libatomic`を別途インストールする必要がある点が案内されている。

## 今後の展望

Lithiumへの移行により、Node.js 26系は安定性を重視する本番環境での採用が推奨される段階に入った。Temporal APIの標準搭載は、エコシステム内のライブラリやフレームワークが日時処理周りで`Date`依存からの移行を進める契機にもなりそうだ。一方で、今回のLTS移行に伴う破壊的変更はすでに26.0.0時点で導入済みであるため、24系などの旧LTSから乗り換える開発者は、非推奨APIの利用状況の点検とビルド環境の要件確認を事前に済ませておくことが望ましい。
