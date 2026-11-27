# Anthropic、Claude Messages APIをPythonからRustに移行しCPU使用量を70%削減
Tags: AI

- Migrating the Messages API to Rust (2026-11-25)
  https://www.anthropic.com/research/migrating-api-to-rust
- Claude rewrote the API that serves Claude. Checking its work was harder (2026-11-25)
  https://thenextweb.com/news/anthropic-claude-messages-api-rust-migration
- Anthropic Says Rust Migration Cut API CPU Use By 70% (2026-11-26)
  https://dataconomy.com/2026/11/26/anthropic-says-rust-migration-cut-api-cpu-use-by-70/

Anthropicは、外部向けClaude APIの中核を担うMessages APIをPythonからRustに書き換えたと発表した。ダウンタイムなしでCPU使用量を約70%削減し、Claude Codeの応答開始までの時間も約20%短縮したという。移行作業のコードの大部分はClaude自身のエージェントが生成し、その検証作業の難しさについても報告されている。
