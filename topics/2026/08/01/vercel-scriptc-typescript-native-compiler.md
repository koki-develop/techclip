# Vercel Labsが「scriptc」を公開、TypeScriptをC言語経由でネイティブバイナリに直接コンパイル
Tags: Programming Languages, OSS

- scriptc (2026-07-26)
  https://github.com/vercel-labs/scriptc

Vercel Labsが、Node.jsやJavaScriptエンジンを一切バンドルせずにTypeScriptから直接ネイティブバイナリ(約170〜200KB)を生成するオープンソースコンパイラ「scriptc」を公開した。LLVMをデフォルトのコード生成基盤とし、ビルド時実行(comptime)やネイティブFFIサポートなどの機能を備え、Hacker Newsでも話題となった。
