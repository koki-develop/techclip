---
date: "2026-05-31T02:28:18+09:00"
title: "Rust 1.96.0リリース — Copy対応の新Range型安定化とCargoのセキュリティ修正"
description: "Rust 1.96.0がリリースされ、RFC 3550に基づくCopy対応の新Range型、assert_matches!マクロの安定化、CargoのCVE修正が含まれる。"
tags:
  - Programming Languages
references:
  - "https://blog.rust-lang.org/2026/05/28/Rust-1.96.0/"
  - "https://linuxiac.com/rust-1-96-introduces-new-copy-friendly-range-types/"
  - "https://alternativeto.net/news/2026/5/rust-1-96-0-new-range-types-stabilized-macros-and-cargo-vulnerability-fixes/"
---

## 概要

Rustチームは2026年5月28日、Rust 1.96.0を正式リリースした。今回のリリースで最も注目すべき変更は、RFC 3550に基づく新しい`core::range`名前空間のRange型の安定化だ。`assert_matches!`および`debug_assert_matches!`マクロも正式に利用可能となり、WebAssemblyターゲットのリンク動作変更、Cargoに関する2件のセキュリティ脆弱性修正も含まれている。

## 新しいCopy対応Range型

従来の`core::ops`に定義されているRange型（`0..5`などのリテラルで生成される型）は、`Iterator`トレイトを直接実装していたため`Copy`トレイトを実装できなかった。これにより、Range値を`Copy`な構造体フィールドに保持することができないという制約があった。

Rust 1.96.0では、RFC 3550にもとづいて`core::range`名前空間に新しいRange型（`Range`、`RangeFrom`、`RangeInclusive`）が安定化された。これらは`Iterator`の代わりに`IntoIterator`を実装する設計に変更されており、`Copy`トレイトが実装されている。これにより、Range値をコピー可能な構造体に格納したり、関数呼び出し後も元の値を使い続けることが可能になる。

現時点では`0..5`のような範囲構文は従来の`core::ops`型を生成し続ける。Rustチームは将来のエディションでこの構文を新しい`core::range`型に移行する計画であり、移行期間中はライブラリ作者に対して公開APIで`impl RangeBounds`を使用し、旧来型・新型の両方をサポートすることが推奨されている。

## assert_matches!マクロの安定化

`assert_matches!`および`debug_assert_matches!`マクロが安定化された。これらのマクロは、ある値が特定のパターンにマッチすることをアサートするためのもので、マッチに失敗した場合は期待パターンと実際の値が表示されるため、従来の`assert!(matches!(...))` よりも診断メッセージが格段に読みやすくなる。なお、使用する際はコード内で明示的にインポートが必要となる。

## WebAssemblyの変更とセキュリティ修正

WebAssemblyターゲットのビルドにおいて、リンカの`--allow-undefined`フラグがデフォルトで削除された。これにより、未定義シンボルが存在する場合はリンクエラーとなり、バグの早期発見に役立つ。

またCargoでは2件の脆弱性が修正された。**CVE-2026-5223**はtarball展開時のシンボリックリンク処理に関連する中程度の脆弱性、**CVE-2026-5222**は正規化URLの認証処理に関連する低程度の脆弱性だ。いずれもサードパーティのレジストリを使用している環境が影響を受けうるもので、crates.ioのみを利用しているユーザーへの影響はない。

## まとめ

Rust 1.96.0はパターンマッチのユーザー体験向上と、長年の課題だったRange型の`Copy`非対応問題に取り組んだリリースだ。新しい`core::range`型はまだ将来のエディション移行に向けた準備段階だが、今からライブラリ設計に組み込むことで将来の移行をスムーズにできる。セキュリティ修正も含まれており、Cargoを使用しているプロジェクトではアップデートが推奨される。
