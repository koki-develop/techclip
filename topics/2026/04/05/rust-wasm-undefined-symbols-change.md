# RustがWebAssemblyターゲットのリンク動作を変更へ、未定義シンボルを将来的にエラーとして扱う
Tags: Programming Languages

- Changes to WebAssembly targets and handling undefined symbols (2026-04-04)
  https://blog.rust-lang.org/2026/04/04/changes-to-webassembly-targets-and-handling-undefined-symbols/

Rustは将来のバージョン（1.96予定）でWebAssemblyリンク時の`--allow-undefined`フラグを廃止し、未定義シンボルをエラーとして報告するよう動作を変更すると発表した。これによりネイティブプラットフォームとの挙動が統一され、WebAssemblyモジュールのビルド時のミス検出が容易になる。
