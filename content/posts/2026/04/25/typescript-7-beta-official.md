---
date: "2026-04-25T02:24:47+09:00"
title: "TypeScript 7.0 Beta正式公開——GoベースコンパイラProject Corsaで従来比10倍の高速化"
description: "MicrosoftがTypeScript 7.0のベータ版を公開し、Goで書き直されたコンパイラにより型チェック速度が従来比約10倍に向上した。"
tags:
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/typescript/announcing-typescript-7-0-beta/"
  - "https://visualstudiomagazine.com/articles/2026/04/21/typescript-7-0-beta-arrives-on-go-based-foundation-with-10x-speed-claim.aspx"
---

## 概要

Microsoftは2026年4月21日、TypeScript 7.0のベータ版を正式に公開した。最大の特徴は、コンパイラ全体をGoで書き直した「Project Corsa（tsgo）」の採用であり、型チェック速度がTypeScript 6.0と比較して約10倍に高速化されている。VS Codeのエディタ起動時間は9.6秒から1.2秒へと大幅に短縮され、メモリ使用量も約半減した。Microsoftは「ベータ段階であってもほとんどのCI/CDワークフローですでに本番利用可能なレベルに達している」と強調しており、Bloomberg、Canva、Figma、Google、Slack、Vercelといった大手企業との協力を通じて「圧倒的にポジティブな」フィードバックが得られているという。

## 技術的な詳細

高速化の根拠はネイティブコード実行と、複数CPUコアにわたる共有メモリ並列化にある。なお、このGoへの移植はゼロからの書き直しではなく、TypeScript 6.0の型チェックロジックを方法的に移植したものであり、セマンティクスの互換性が維持されている。

並列処理は次の3つの軸で制御できる。型チェックワーカーはデフォルト4個で動作し、`--checkers`フラグで数を調整可能。複数プロジェクトを同時にコンパイルする際は`--builders`フラグを使う。デバッグやリソース制約のある環境向けには`--singleThreaded`でシングルスレッドモードに切り替えられる。

コマンドラインツールは従来の`tsc`ではなく`tsgo`として提供され、npm経由で次のようにインストールできる。

```
npm install -D @typescript/native-preview@beta
```

VS Code向けの統合拡張機能も提供されており、エディタ上でもパフォーマンス向上の恩恵を受けられる。

## 破壊的変更

TypeScript 7.0ではいくつかの厳格なデフォルト変更が導入された。`strict`モードがデフォルトで有効化され、ES5をターゲットとする設定が廃止される。また、AMD・UMD・SystemJSのモジュール形式のサポートも終了する。これらはレガシーな構成との決別を意味しており、既存プロジェクトでの採用には移行コストが伴う可能性がある。

## 今後の見通し

Microsoftはベータ公開後数週間以内にリリース候補版を、約2ヶ月以内に安定版をリリースする予定を示している。Goベースのコンパイラへの移行はTypeScriptエコシステムに大きな転換をもたらすものであり、大規模コードベースを抱える開発チームにとって特に恩恵が大きいと見られている。
