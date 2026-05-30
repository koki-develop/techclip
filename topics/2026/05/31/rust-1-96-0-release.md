# Rust 1.96.0リリース — Copy対応の新Range型とassert_matches!マクロが安定化
Tags: Programming Languages

- Announcing Rust 1.96.0 (2026-05-28)
  https://blog.rust-lang.org/2026/05/28/Rust-1.96.0/
- Rust 1.96 Introduces New Copy-Friendly Range Types (2026-05-28)
  https://linuxiac.com/rust-1-96-introduces-new-copy-friendly-range-types/
- Rust 1.96.0: new range types, stabilized macros, and cargo vulnerability fixes (2026-05-28)
  https://alternativeto.net/news/2026/5/rust-1-96-0-new-range-types-stabilized-macros-and-cargo-vulnerability-fixes/

RFC 3550に基づく新しいCopy対応Range型（`core::range::Range`等）が安定化され、`assert_matches!`・`debug_assert_matches!`マクロも正式利用可能になった。またCargoのセキュリティ脆弱性CVE-2026-5223およびCVE-2026-5222の修正も含まれている。
