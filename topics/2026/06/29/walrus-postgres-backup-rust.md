# ClickHouseがPostgreSQLバックアップツール「WAL-G」をRustで書き直した「WAL-RUS」をOSSとして公開
Tags: OSS

- Why we rewrote WAL-G for Postgres backups in Rust: Meet WAL-RUS (2026-06-25)
  https://clickhouse.com/blog/walrus-postgres-backups-in-rust
- WAL-RUS: a Rust Rewrite of WAL-G for PostgreSQL Backups | Hacker News (2026-06-28)
  https://news.ycombinator.com/item?id=48702848

ClickHouseがGoで実装されたPostgreSQLバックアップツール「WAL-G」をRustで全面的に書き直した「WAL-RUS」をオープンソースとして公開した。ピーク仮想メモリ使用量をWAL-Gと比べて70%以上削減しながら、既存のWAL-Gアーカイブとの完全な互換性を維持しており、Hacker Newsでも注目を集めている。
