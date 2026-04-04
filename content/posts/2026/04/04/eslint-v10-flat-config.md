---
date: "2026-04-04T10:37:37+09:00"
title: "ESLint v10正式リリース——旧`.eslintrc`設定を完全廃止、フラットコンフィグへの移行が完了"
description: "ESLint v10が正式リリースされ、レガシー設定システムの完全廃止、モノレポ対応の改善、JSX参照追跡の強化など多くの変更が加えられた。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/04/eslint-10-release/"
---

## 概要

ESLint v10が正式にリリースされ、長期にわたる移行期間を経てフラットコンフィグへの完全移行が完了した。最大の破壊的変更は、旧来の`.eslintrc`設定システムの完全廃止だ。互換レイヤーとして提供されていた`LegacyESLint`が削除され、`Linter`クラス上の`defineParser()`・`defineRule()`・`defineRules()`・`getRules()`といったメソッドも取り除かれた。また`shouldUseFlatConfig()`は無条件で`true`を返すようになった。まだ`.eslintrc`を利用しているチームはv10へのアップグレード前に移行を済ませる必要があり、公式の移行ツール`npx @eslint/migrate-config .eslintrc.json`を使えば`eslint.config.mjs`ファイルを自動生成できる。

## 技術的な変更点

設定ファイルの探索ロジックも改善された。従来はカレントワーキングディレクトリを起点に検索していたが、v10ではリントするファイルのディレクトリから順に検索するよう変更された。これによりパッケージごとに異なるルールを持つモノレポ構成での利便性が高まる。

JSX識別子を変数参照として認識する機能も追加された。これによりJSXのみで使用されるコンポーネントが`no-unused-vars`ルールで誤検知される問題が解消され、`@eslint-react/jsx-uses-vars`などのコミュニティワークアラウンドが不要になる。テスト基盤面では`RuleTester` APIに`requireMessage`・`requireLocation`・`requireData`の新オプションが追加され、プラグイン開発者がより厳密なテスト定義を書けるようになった。

Node.jsの対応バージョンは`^20.19.0 || ^22.13.0 || >=24`に絞られ、v21.xおよびv23.xは非対応となった。

## エコシステムと競合状況

移行に際してエコシステム側の課題も浮き彫りになった。`eslint-plugin-react`やNext.jsが標準で使用する`eslint-config-next`がv10のピア依存宣言に初期対応していなかったため、Reactを利用する開発者の間でインストール時の競合が発生した。コミュニティからは「フラットコンフィグの発想は良いが移行パスが難しかった」という声も上がっており、プラグインごとの実装差異が不安要素として挙げられている。

競合ツールとしてはRust製の[Biome](https://biomejs.dev/)や[Oxlint](https://oxc.rs/)が台頭しており、OxcはCPUコア数によっては50〜100倍の性能改善をうたっている。ただしルールカバレッジの面ではESLintの広大なエコシステムに及ばないため、既存のルールセットへの依存度によって乗り換えの判断が分かれる状況が続いている。
