# SQLite本体にベクトル検索拡張「vec1」が統合
Tags: OSS, Programming Languages

- SQLite本体にベクトル検索拡張 vec1 がやってきた (2026-10-11)
  https://zenn.dev/mattn/articles/6e9996319ac099

SQLite公式のベクトル検索拡張「vec1」がソースツリーに統合された。外部依存のないポータブルなC実装で、L2距離・コサイン距離による近似最近傍探索(IVFADC+OPQ量子化、SIMD最適化)を仮想テーブル経由で利用できるようになり、組み込みDBのままベクトル検索が行える。
