---
date: "2026-05-04T02:21:41+09:00"
title: "NestJS v12ロードマップ公開——ESM完全移行・Zodネイティブ対応・VitestデフォルトでNode.jsフレームワークを刷新"
description: "NestJS v12のロードマップが公開され、CommonJSからESMへの完全移行を筆頭に、Zod/Valibot対応のネイティブバリデーション、JestからVitestへの切り替えなど、エコシステム全体の大規模なモダナイズが2026年Q3を目標に計画されている。"
tags:
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/04/nestjs-12-roadmap-esm/"
  - "https://github.com/nestjs/nest/pull/16391"
---

## 概要

NestJS の作者 Kamil Myśliwiec 氏は、メジャーバージョン v12 のロードマップをドラフトプルリクエスト（PR #16391）として公開した。リリース目標は2026年Q3初頭とされており、CommonJS（CJS）から ECMAScript Modules（ESM）への完全移行を中心に、テストフレームワーク・リンター・バンドラーの全面刷新、そしてモダンなバリデーションライブラリのネイティブサポートなど、エコシステム全体に及ぶ大規模な変更が含まれる。この発表はX（旧Twitter）で800件を超えるいいねを集めるなど、コミュニティから大きな注目を浴びた。

## ESM完全移行——Node.jsの「require(esm)」が後押し

v12 最大の変更は、全公式パッケージを CommonJS から ESM へ移行することだ。Myśliwiec 氏は「Node.js の `require(esm)` サポートが、この移行に必要な最後のピースだった」と述べており、CJS コードから ESM モジュールを `require()` で読み込める Node.js の新機能が実現の鍵となった。これにより、既存の CJS ベースのプロジェクトは大幅な書き換えなしに v12 へ移行できる見込みで、互換性への懸念を最小限に抑えながら段階的な採用が可能になる。

## 新機能——Standard Schema によるネイティブバリデーション

v12 では `@Body`・`@Query`・`@Param` などのルートデコレータに `schema` オプションが追加され、Standard Schema に準拠したバリデーションライブラリを直接利用できるようになる。これにより、従来の `class-validator` に代わって Zod・Valibot・ArkType といったモダンなライブラリを公式にサポートする。型安全なスキーマ定義ライブラリが急速に普及している近年のトレンドに対応した機能追加であり、既存の NestJS プロジェクトにおけるバリデーション層の柔軟性が大幅に向上する。

## ツールチェーンの刷新——Vitest・Oxlint・Rspack

テスト・リンティング・バンドリングの各レイヤーでデフォルトツールが入れ替わる。ESM プロジェクトではテストフレームワークが Jest から Vitest に切り替わる（既存の CJS プロジェクトは Jest を継続利用できる）。Vitest は TypeScript デコレータの処理に OXC を採用しており、ESM 環境との親和性が高い。リンターは Rust 製の高速ツールである Oxlint が ESLint に取って代わり、バンドラーは Webpack から Rspack へ移行してビルド速度の大幅な向上が見込まれる。コミュニティからは Bun や Biome の CLI オプションへの追加を求める声も上がっており、今後の検討が期待される。

## その他の改善点とリリース見通し

上記の主要変更に加え、マイクロサービス向けの NATS v3 対応、Express アダプターへのグレースフルシャットダウンサポート、WebSocket の切断理由パラメーター、パイプの `transform` 型安全性の向上なども予定されている。正式リリース前には `next` タグでパッケージが先行公開される予定で、早期採用者がフィードバックを提供できる機会が設けられる見込みだ。
