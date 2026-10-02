---
date: "2026-10-02T18:14:45+09:00"
title: "Rust 1.99.0リリース、C互換の可変長引数関数とunsizedポインタのレイアウト取得APIを安定化"
description: "Rust 1.99.0が公開され、C ABIの可変長引数関数(extern \"C\" variadics)と生ポインタからレイアウト情報を取得する3つのAPIが安定化された。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://blog.rust-lang.org/2026/10/01/Rust-1.99.0/"
---

## 概要

Rust開発チームは10月1日、プログラミング言語Rustの新バージョン1.99.0を正式リリースした。今回の目玉は、「C」および「C-unwind」ABIにおいてC言語互換の可変長引数関数(`extern "C" variadics`)をRust自体で定義できるようになった点だ。これまでRustからCの可変長引数関数を呼び出すことはできても、Rust側で可変長引数を受け取る関数を定義してCに公開することはできなかった。この機能により、`...`を用いて任意個数の引数を受け取る関数をRustで実装し、Cライブラリに関数ポインタとして渡すといった相互運用がより自然に行えるようになる。

## 技術的な詳細

可変長引数の実体は新たに安定化された`core::ffi::VaList`型で表され、C側の`va_list`とABIレベルで互換性を持つ。可変長引数から読み取り可能な型は`VaArgSafe`トレイトを実装する型に制限され、未定義動作を防ぐ設計になっている。あわせて、生ポインタからサイズ・アラインメントなどのレイアウト情報を取得する3つのAPI、`core::alloc::Layout::for_value_raw`、`core::mem::size_of_val_raw`、`core::mem::align_of_val_raw`も安定化された。これらはサイズ既知の型だけでなく、スライスやトレイトオブジェクトのような動的サイズ型(unsized型)に対しても安全に使用できるよう、呼び出し側が満たすべき安全要件が明確化されている。

## その他の変更点

今回のリリースでは他にも実用的なAPIが多数安定化された。`Box<[T; N]>`に対する`IntoIterator`実装(値渡し・参照・可変参照の3種)、`VecDeque::retain_back`、`Vec`をキャパシティ・長さ・ポインタへ分解・再構築する`Vec::into_parts`/`Vec::from_parts`、同様の`Box::into_non_null`/`Box::from_non_null`、UTF-8検証に失敗したバイト列を所有権付きで文字列化する`String::from_utf8_lossy_owned`と`FromUtf8Error::into_utf8_lossy`、ファイルのタイムスタンプを設定する`std::fs::set_times`/`set_times_nofollow`などが新たに利用可能になった。また`StepBy<I>`イテレータへの`FusedIterator`実装も追加されている。Cとの相互運用性を高めるこれらの変更により、低レベルなFFIコードを書く開発者にとって、より安全かつ簡潔な実装が可能になりそうだ。
