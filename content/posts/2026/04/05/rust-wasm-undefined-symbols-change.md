---
date: "2026-04-05T10:37:07+09:00"
title: "Rust 1.96でWebAssemblyの未定義シンボルがデフォルトエラーに、--allow-undefinedフラグを廃止"
description: "RustはWebAssemblyターゲット向けリンカの--allow-undefinedフラグを廃止し、Rust 1.96（2026年5月28日予定）から未定義シンボルをデフォルトでエラーとして扱うよう変更する。"
tags:
  - Programming Languages
references:
  - "https://blog.rust-lang.org/2026/04/04/changes-to-webassembly-targets-and-handling-undefined-symbols/"
---

## 概要

Rustは全WebAssemblyターゲットにおいて、リンカオプション `--allow-undefined` フラグを廃止すると発表した。Rust 1.96（2026年5月28日リリース予定）から、未定義シンボルはデフォルトでエラーとして報告されるようになる。この変更はネイティブプラットフォームとの動作の一貫性を高め、WebAssemblyモジュールのビルド時における誤設定やミスの早期発見を可能にするものだ。

## 変更の背景と理由

従来、WebAssemblyバイナリの生成には `wasm-ld` リンカが使われており、`--allow-undefined` フラグによって未解決シンボルをエラーとせず、WebAssemblyモジュールのインポートとして変換する動作が許容されていた。たとえば、Rustコード中で外部C関数 `mylibrary_init` を宣言した場合、リンク時にエラーを出さず `(import "env" "mylibrary_init" ...)` としてWasmモジュールへ埋め込まれる仕組みだった。

この動作にはいくつかの問題点があった。関数名のタイポがあってもコンパイルエラーにならず、実行時に壊れたシンボルがインポートされるリスクがあった。また、必要なライブラリが欠落していても警告が出ずに動作しないモジュールが生成される可能性があった。Rustの公式ブログでは「misconfiguration or mistakes in building can result in broken WebAssembly modules being produced（ビルドの誤設定やミスが壊れたWebAssemblyモジュールの生成につながる）」と指摘している。ネイティブプラットフォームでは未定義シンボルはデフォルトでエラーとなるため、WebAssemblyだけが異なる挙動を取っていた点も問題視されていた。

## 移行方法と影響範囲

Rust公式は、大多数のユーザーはこの変更による影響を受けないとしている。ただし、`--allow-undefined` の動作に明示的に依存していた場合は対応が必要だ。対処法として2つの方法が案内されている。

1つ目は `#[link]` 属性を使った明示的なモジュール指定で、インポートするシンボルが属するWasmモジュール名を `wasm_import_module` で明記する方法だ。2つ目は `-Clink-arg=--allow-undefined` をコンパイラフラグとして渡すことで、旧来の動作を維持する方法だ。問題が生じた場合は `rust-lang/rust` リポジトリへのissue報告が推奨されている。変更はすでにPR #149868としてまとめられており、ナイトリービルドへの統合を経てRust 1.96での正式リリースが計画されている。
