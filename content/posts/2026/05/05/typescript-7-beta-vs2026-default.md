---
date: "2026-05-05T02:37:31+09:00"
title: "TypeScript 7 BetaがVisual Studio 2026 InsidersのデフォルトSDKに、Goによるネイティブ実装で最大10倍高速化"
description: "Visual Studio 2026 18.6 Insiders 3でTypeScript 7 Betaがデフォルトの組み込みSDKとして採用され、Go言語によるネイティブ実装によりコンパイル最大10倍・プロジェクト読み込み8倍の高速化が実現された。"
tags:
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/visualstudio/typescript-7-beta-now-enabled-by-default-in-visual-studio-2026-18-6-insiders-3/"
---

## 概要

Microsoftは2026年4月30日、Visual Studio 2026 18.6 Insiders 3にてTypeScript 7 Betaをデフォルトの組み込みSDKとして有効化したことを発表した。これは、TypeScriptコンパイラをJavaScriptからGo言語でネイティブ実装し直す大規模なアーキテクチャ刷新の成果であり、IDEから直接その恩恵を受けられるようになる重要なマイルストーンである。独自のTypeScriptバージョンを指定していないすべてのTypeScript/JavaScriptプロジェクトがこの新しいネイティブコンパイラを使用するようになる。

## パフォーマンスの大幅な向上

新しいネイティブコンパイラは、従来のJavaScript実装と比較して顕著なパフォーマンス改善をもたらす。大規模コードベースにおけるコンパイル時間は最大10倍短縮され、メモリ消費量も削減される。また、プロジェクトの読み込み時間は約8倍高速化された。

IDE上での体験においても、IntelliSenseや補完候補の表示が特に大規模プロジェクトで迅速になり、ソリューション全体を対象とした「すべての参照を検索」や「定義へ移動」のナビゲーションもより高速に動作する。コードを入力しながらリアルタイムにエラー診断が更新されるため、開発者の生産性が全体的に向上する。

## バージョン管理と既知の制限

従来のTypeScript 6.xを引き続き使用したい場合は、npmで`typescript`パッケージをインストールするか、特定のネイティブバージョンには`@typescript/native-preview`パッケージを利用できる。機能を無効化する場合は、「ツール > オプション > プレビュー機能」から「Enable JavaScript/TypeScript Native Language Service Preview」をオフにすることで切り替え可能だ。

現時点ではプレビュー段階であるため、いくつかの既知の問題がある。`.cshtml`のスクリプトタグ内でのIntelliSense補完が機能しない場合があること、クイックフィックスやコードリファクタリング機能が未実装であること、ナビゲーションバーにドキュメントシンボルが表示されないこと、CodeLensの参照カウントが宣言の上に表示されないこと、JSDoc自動生成が動作しないこと、ファイル・フォルダのリネーム時にimportが一貫して更新されないことなどが挙げられる。問題に遭遇した場合は、[typescript-go GitHubリポジトリ](https://github.com/microsoft/typescript-go/issues)またはVisual StudioのDeveloper Communityプラットフォームへのフィードバックが推奨されている。
