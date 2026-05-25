---
date: "2026-05-26T02:36:54+09:00"
title: "Angular 22 RC公開——Signal Forms安定化やセレクターレスコンポーネントなどSignal-First設計への転換が進む"
description: "Angular 22のリリース候補（22.0.0-rc.1）が公開され、Signal Formsの安定化やセレクターレスコンポーネントなど、Signals中心の開発モデルへの転換が一段と進む見込みだ。"
tags:
  - Programming Languages
references:
  - "https://www.herodevs.com/blog-posts/angular-v19-goes-eol-may-19-angular-22-is-coming-the-same-month-here-is-how-to-navigate-both"
  - "https://versionlog.com/angular/22.0/"
  - "https://arc.dev/employer-blog/angular-latest-version-your-friendly-guide-to-new-features-and-updates-in-2026/"
---

## 概要

Angular 22のリリース候補（22.0.0-rc.1）が2026年5月20日に公開され、安定版リリースを目前に控えている。v22では Signal Forms（リアクティブフォームの新API）の安定化と、セレクターレスコンポーネントの導入が予定されており、Angular 21で先行投入されたゾーンレス変更検出のデフォルト化やVitestへのテストランナー切り替えと合わせて、「Signal-First」設計への転換が一段と進む節目のリリースとなる。

なお、Angular 19は2026年5月19日にEOL（サポート終了）を迎えており、以降はセキュリティパッチも提供されない。Angularチームはv19在籍中に少なくとも3件の高深刻度CVEが発生した事実を挙げ、EOL後の継続利用リスクを強調している。

## 主要な新機能・変更点

**Signal Forms の安定化**は v22 最大のハイライトとして予定されている。Angular 21では `@angular/forms/signals` 経由で実験的 API として提供されていたが、v22 では従来の `ReactiveFormsModule` に代わる Signals ベースの新しいリアクティブフォーム API として安定版に到達する見込みだ。`valueChanges.pipe(takeUntil(...))` のような RxJS パターンが不要になり、フォームの状態管理がよりシンプルかつ型安全になる。

**ゾーンレス変更検出のデフォルト化**は Angular 21 ですでに導入済みで、v22 でも継続される。新規プロジェクトでは Zone.js が不要となり、Signals ベースの変更検出機構がデフォルトで有効になる。Zone.js の除去によってバンドルサイズが削減され、変更検出のオーバーヘッドも大幅に低減される。既存プロジェクトへの自動適用はなく、段階的な移行が可能だ。

**セレクターレスコンポーネント**の導入により、`selector` プロパティを省略したコンポーネント定義が可能になる。ルーターや動的ロードなど、テンプレートへの直接埋め込みが不要なユースケースで冗長なセレクター定義を省けるようになる。

**Vitestへの移行**は Angular 21 で実施済みで、v22 でも継続される。Karma は完全廃止となり Vitest が標準テストランナーとなっている。Vitest は Karma と比較して5〜10倍高速とされており、開発者体験の大幅な改善が期待できる。

## 移行上の注意点

Angular 21 で導入された以下の破壊的変更は、v22 への移行時にも引き続き考慮が必要となる。

- **OnPush がデフォルト変更検出戦略に**: 新規コンポーネントのデフォルトが `ChangeDetectionStrategy.OnPush` となる
- **`ng-reflect-*` 属性の削除**: デバッグ用属性が本番ビルドから除去される
- **`NgModuleFactory` の削除**: 旧来の NgModule ベース API が完全廃止
- **HammerJS 統合の削除**: タッチジェスチャーサポートが組み込みから分離
- **Node.js v22.22.0 以上（または v24.13.1 以上）が必須**: 旧バージョンの Node.js はサポート対象外となる

NgModule を多用する既存の大規模プロジェクトや、サードパーティライブラリへの依存が強いチームにとっては、移行コストが相応に発生する可能性がある。移行の優先度はアーキテクチャの複雑さとデプロイプロセスを踏まえて評価することが推奨される。

## 今後の展望

Angular はおよそ6ヶ月ごとにメジャーバージョンをリリースするサイクルを維持しており、v22 は Signal 中心の開発モデルへの移行をほぼ完結させる節目のリリースと位置付けられる。ゾーンレス・Signal Forms・セレクターレスという三位一体の変更が揃ったことで、今後の新規プロジェクトは最初からフルSignal構成で構築できる環境が整った。既存プロジェクトの段階的移行を支援するツールや公式ガイドの充実が、次のフェーズにおける課題となるだろう。
