---
date: "2026-05-22T02:43:51+09:00"
title: "Vercel Labsがシステム言語「Zero」を公開——AIエージェントがコンパイルエラーをJSONで直接処理"
description: "Vercel LabsがAIエージェントによる自律的なコード修復・デプロイを念頭に設計したシステムプログラミング言語「Zero」をApache 2.0ライセンスで公開した。"
tags:
  - Programming Languages
  - AI
references:
  - "https://www.marktechpost.com/2026/05/17/vercel-labs-introduces-zero-a-systems-programming-language-designed-so-ai-agents-can-read-repair-and-ship-native-programs/"
  - "https://www.techtimes.com/articles/316793/20260518/vercel-labs-zero-compiler-speaks-json-ai-agents-closing-human-translation-gap-agentic-coding.htm"
---

## 概要

Vercel Labsは2026年5月15日、AIエージェントによる自律的なコード読み取り・修復・デプロイを主眼に設計したシステムプログラミング言語「Zero」をv0.1.1としてリリースした。CやRustと同じ低レベル設計空間に位置し、ネイティブ実行可能ファイルにコンパイルされる。開発者はVercel LabsのChris TateとMatt Van Hornで、ソースコードはApache 2.0ライセンスでGitHub（vercel-labs/zero）に公開されている。ファイル拡張子は`.0`。

従来のプログラミング言語は「人間がエラーメッセージを読み、警告を解釈し、スタック出力を手動でトレースしてバグを修正する」ことを前提に設計されてきた。Zeroはその前提を覆し、AIエージェントが中間的な人間の翻訳なしにコンパイラ出力を処理できる構造を実現している。

## JSONによる機械可読な診断出力

Zeroの最大の特徴は、コンパイラが構造化JSONで診断情報を出力する点にある。`zero check --json`を実行すると、以下のような形式でデータが返される。

```json
{
  "ok": false,
  "diagnostics": [{
    "code": "NAM003",
    "message": "unknown identifier",
    "line": 3,
    "repair": { "id": "declare-missing-symbol" }
  }]
}
```

各診断には安定したエラーコード識別子と型付きの修復メタデータが含まれる。エラーコードはコンパイラバージョン間で一貫性を保つよう設計されており、AIエージェントは同じコードに対して一度学習すれば再学習が不要になる。これに加え、`zero fix --plan --json`で機械可読な修復計画を生成し、`zero explain <code>`で診断コードの詳細説明をクエリできる。さらに`zero skills`コマンドは、インストール済みのコンパイラバージョンに同期したエージェント向けワークフロー資料をCLIから直接提供し、外部ドキュメントのスクレイピングを不要にする。

## 技術的な設計方針

能力ベースのI/Oモデルを採用しており、副作用は関数シグネチャに明示的に宣言される。

```
pub fun main(world: World) -> Void raises {
  check world.out.write("hello from zero\n")
}
```

コンパイル時に利用不可能な能力は拒否されるため、AIエージェントが関数の振る舞いを記号レベルで把握しやすい。バイナリサイズは10KiB未満に最適化され、強制的なガベージコレクションや隠れた割り当て、非同期処理を排除することで予測可能なメモリ管理を実現している。静的ディスパッチを採用し、実行時の挙動が推論しやすい設計になっている。

## 現状と課題

現時点でZeroはv0.1.1の実験段階にあり、コンパイラと言語仕様は未安定化である。パッケージレジストリは初期段階、クロスコンパイルは文書化されたターゲットに限定されており、VS Code拡張機能は構文ハイライトのみ対応している。開発者コミュニティからは「LLMはすでにRustやPythonのエラーを処理できる」という指摘や、メモリ安全性保証の実装の未成熟さへの懸念も上がっており、実用化に向けてはこれらの課題への対応が求められる。
