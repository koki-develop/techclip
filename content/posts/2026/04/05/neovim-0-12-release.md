---
date: "2026-04-05T10:37:07+09:00"
title: "Neovim v0.12.0リリース — 内蔵プラグインマネージャー、LSP強化、Lua HTTP APIなど多数の新機能"
description: "Neovim v0.12.0が正式リリースされ、組み込みパッケージマネージャー`vim.pack`、LSPのインライン補完・コードレンズ改善、`vim.net.request()`によるHTTP操作など多数の機能強化が加わった。"
tags:
  - OSS
  - Dev Tools
references:
  - "https://github.com/neovim/neovim/releases/tag/v0.12.0"
  - "https://alternativeto.net/news/2026/3/neovim-0-12-has-been-released-with-a-built-in-plugin-manager-major-lsp-and-ui-upgrades/"
---

## 概要

Neovimは2026年3月29日、メジャーリリースとなる**v0.12.0**を公開した。今回の最大のハイライトは、外部ツールへの依存を不要にする**組み込みパッケージマネージャー `vim.pack`** の導入だ。これまでlazy.nvimやpacker.nvimといったサードパーティのプラグインマネージャーに頼っていた管理フローを、Neovim本体で完結できるようになった。コミュニティからの反応はGitHub上で525件以上のリアクションを集めるなど、非常に好評を博している。

## LSP・補完の大幅強化

LSPまわりの改善も今回の目玉だ。補完候補にカラーシンボルのプレビューや**インライン補完**が追加されたほか、新しい対話型コマンド `:lsp` によってLSPクライアントを一元管理できるようになった。コードレンズが仮想行として表示されるよう変更されたことで視認性も向上した。さらに `textDocument/diagnostic`・ `textDocument/documentColor`・ワークスペース診断・動的登録など多数のLSP仕様への対応も追加されている。デフォルトキーバインドには `grt`（型定義へジャンプ）と `grx`（コードレンズ実行）が新たに加わった。

## Lua APIの拡充とHTTP対応

Lua APIにも注目すべき追加がある。`vim.net.request()` の追加により、外部ライブラリを使わずにNeovim内から直接HTTPリクエストを発行できるようになった。そのほか `vim.list.unique()`・`vim.list.bisect()` などのリスト操作関数、`vim.text.diff()`（旧 `vim.diff`）、フローティングウィンドウへのステータスライン表示・タブページ間移動のサポートなども追加された。新オプションとして `'autocomplete'`・`'pummaxwidth'`・`'pumborder'`・`'busy'` などが導入されている。

## パフォーマンス改善と実験的Zigビルド

パフォーマンス面では、`i_CTRL-R` によるレジスタ挿入が従来のユーザー入力シミュレーション方式から貼り付け方式に変わり**約10倍高速化**。LPeg実装によりglobパターンマッチングが**約50%高速化**された。LSPはトークンリクエストを表示中のビューポートに限定するよう最適化され、帯域幅の節約にも貢献している。また実験的機能として**Zigベースのビルドシステム**が導入された。

## 破壊的変更と注意点

既存の設定に影響する破壊的変更もいくつか含まれる。`vim.diagnostic.disable()` などの旧来のDiagnostics APIが削除され、JSONのnull値が `nil` から `vim.NIL` に変更された。セマンティックトークン関数が `start()/stop()` から `enable()` にリネームされるなど、プラグイン開発者は対応が必要になる場合がある。Windowsでは外部コマンド実行時にカレントディレクトリを検索しなくなるセキュリティ強化も施された。アップグレード前に公式チェンジログでの確認が推奨される。
