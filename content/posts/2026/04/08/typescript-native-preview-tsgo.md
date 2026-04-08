---
date: "2026-04-08T10:38:28+09:00"
title: "TypeScriptのGoネイティブ実装「tsgo」がnpmでプレビュー公開、最大10倍の高速化を実現"
description: "MicrosoftがGoで書き直したTypeScriptコンパイラ「tsgo」のネイティブプレビューをnpmパッケージとして公開し、多くのプロジェクトで10倍以上のコンパイル速度向上を実証した。"
tags:
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/typescript/announcing-typescript-native-previews/"
  - "https://devblogs.microsoft.com/typescript/progress-on-typescript-7-december-2025/"
---

## 概要

Microsoftは2025年5月、TypeScriptコンパイラをGoで書き直したネイティブ実装「tsgo」（コードネーム「Corsa」）のプレビュー版をnpmパッケージ `@typescript/native-preview` として公開した。2025年3月に最初の発表がなされて以降、着実に開発が進んでおり、今回のリリースはTypeScript 7に向けた重要なマイルストーンとなる。CLIツールは `npm install -D @typescript/native-preview` でインストールでき、VS Code向けの拡張機能「TypeScript (Native Preview)」もマーケットプレイスから入手可能だ。

## パフォーマンスの大幅向上

最も注目される成果はコンパイル速度の劇的な改善だ。Sentryのコードベースでのテストでは、従来のJavaScript実装が72秒以上かかっていたビルドが、ネイティブ実装ではわずか約6.8秒に短縮された。Microsoftは「ほとんどのプロジェクトで10倍以上の高速化」を達成したと述べており、大規模なTypeScriptプロジェクトを扱う開発者にとって大きなメリットとなる。

## 技術的な詳細と現在の対応状況

型チェック機能の大部分がポートされており、ほとんどのプロジェクトで既存と同等のエラー検出が可能だ。JSXのサポートも追加され、Reactコードベースの型チェックにも対応している。JavaScriptファイルのJSDocを通じた型チェックや、コード補完・定義ジャンプ・ホバー情報などのエディタ機能も基本的に動作する。内部アーキテクチャとして、JavaScriptクライアントとRust製の同期RPCモジュール `libsyncrpc` を組み合わせたIPCベースのAPIレイヤーが構築されている。

初期プレビューの時点では `--build` モードやエディタ機能の一部が未実装だったが、2025年12月のアップデートで `--build` モード・`--incremental`・プロジェクトリファレンスの移植が完了し、自動インポート・全参照検索・リネームも再実装されて日常的に使用可能な状態となった。一方、型宣言ファイルの生成（declaration emit）は依然として未対応であり、ダウンレベルターゲットへのトランスパイルは `es2021` 以降に限定されている。また、非推奨となっている `node`/`node10` モジュール解決モードはサポートされないため、`bundler` または `nodenext` への移行が必要となる。

## 今後の展開

プレビューは毎晩ビルドが公開される予定で、最終的にはTypeScript 7として正式リリースされる。`--build` モードは2025年末までに移植が完了しており、残る主要機能としてはフルの `--target` サポート（`es2015` まで遡る対応）や型宣言ファイルの生成などが開発中だ。開発チームはフィードバックを積極的に求めている。ネイティブバイナリによる高速化はTypeScriptエコシステム全体の開発体験を大きく向上させる可能性があり、今後の進捗に注目が集まる。
