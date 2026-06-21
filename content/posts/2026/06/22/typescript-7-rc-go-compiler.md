---
date: "2026-06-22T02:36:20+09:00"
title: "TypeScript 7.0 RCリリース：GoによるネイティブコンパイラがVS Codeのビルドを77秒から7.5秒に短縮"
description: "MicrosoftがGoで書き直したTypeScriptコンパイラのRC版を公開し、既存のJavaScript実装比で最大10倍超の高速化と大幅なメモリ削減を実現した。"
tags:
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/typescript/announcing-typescript-7-0-rc/"
  - "https://www.techtimes.com/articles/318666/20260618/typescript-70-rc-ships-go-compiler-cuts-vs-code-build-time-77-seconds-seven.htm"
  - "https://www.digitalapplied.com/blog/typescript-7-0-rc-go-native-compiler-2026-upgrade-guide"
---

## 概要

Microsoftは2026年6月18日、TypeScript 7.0のリリース候補（RC）を公開した。最大の変更点は、コンパイラを従来のTypeScript（自己ホスト型）からGoで書き直したことにある。「Project Corsa」と呼ばれるこのプロジェクトは、既存の型チェックセマンティクスを保ちながら移植（再設計ではなく）を行い、ネイティブバイナリの実行速度（3〜4倍）と、Goのゴルーチンによる共有メモリ並列処理（2〜3倍）を組み合わせることで、最大10倍超の高速化を達成した。Bloomberg、Figma、Google、Slack、Vercelなど複数の大規模チームが同様のスピードアップを報告している。

## パフォーマンスの改善

パフォーマンス向上の数値は顕著だ。約150万行のコードを持つVS Codeリポジトリでは、ビルド時間が77.8秒から7.5秒へと10.4倍高速化された。エディタのプロジェクト読み込みは9.6秒から1.2秒へ8倍改善し、メモリ使用量はおよそ半減した。言語サーバーの信頼性も20倍以上向上し、失敗件数が大幅に減少している。インストールは `npm install -D typescript@rc` で行えるほか、VS Code向けの「TypeScript Native Preview」拡張機能から即座に利用できる。

## GoをRustではなく採用した理由

言語選定においてGoとRustが候補に挙がったが、TypeScriptコンパイラが内部で持つ抽象構文木（AST）とシンボルテーブル間の循環参照がRustの所有権モデルと相性が悪く、大幅な構造変更なしには実現できない状況だった。一方、ガベージコレクションを持つGoは既存のアーキテクチャに自然にマッピングでき、型チェックのセマンティクスを維持したまま約1年でのポートを可能にした。

## 新機能と並列処理フラグ

7.0では並列処理を制御する3つの新しいコンパイラフラグが追加された。`--checkers N`（デフォルト: 4）は型チェッカーの並列ワーカー数、`--builders N`（デフォルト: 16）はプロジェクト参照の並列ビルド数を制御し、`--singleThreaded` はデバッグやリソースが限られたCI環境向けに並列処理を無効化する。`--watch` モードはParcelのファイルウォッチャーをGoに移植したものを使用しており、ポーリングベースの従来実装に比べてリソース効率が大幅に向上した。

## 破壊的変更と移行上の注意点

TypeScript 5.xから移行するチームは `tsconfig.json` の見直しが必要になる。主な変更点は、`rootDir` のデフォルトが `./` になった（`src/` を使うプロジェクトは明示的に設定が必要）、`types` のデフォルトが空配列になり `@types/` パッケージの自動インクルードがなくなった点などだ。また、`target: es5` や `moduleResolution: node`、`baseUrl`、AMD/UMD/SystemJS形式のモジュールは削除されている。テンプレートリテラル型の推論では絵文字がUTF-16サロゲートペアではなく1コードポイントとして扱われるようになった。

重要な制約として、typescript-eslintやts-morphなどのツールが依存するプログラマティックAPIの安定化はTypeScript 7.1を予定しており、「少なくとも数か月先」とされている。そのため現時点では `tsc` CLIとCI型チェックに7.0を使いながら、typescript-eslintなどのツールは `npm install -D typescript@npm:@typescript/typescript6` でインストールした6.0のエイリアスを維持する段階的な移行が推奨される。GA版は今後約1か月以内のリリースが見込まれている。