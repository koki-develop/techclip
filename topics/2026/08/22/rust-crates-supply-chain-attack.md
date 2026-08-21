# Rustのクレートエコシステムでサプライチェーン攻撃、著名開発者アカウント侵害で2億4500万DL超のクレートにビルド時マルウェア混入
Tags: Security, OSS

- Rust Supply Chain Attack Puts Build-Time Malware in Crates with 245 Million Downloads (2026-08-21)
  https://thehackernews.com/2026/08/rust-supply-chain-attack-puts-build.html
- Hackers poison arrayref Rust crate to push infostealer malware (2026-08-20)
  https://www.bleepingcomputer.com/news/security/hackers-poison-arrayref-rust-crate-to-push-infostealer-malware/
- Hackers poison popular Rust crates to steal developers' credentials (2026-08-21)
  https://www.theregister.com/security/2026/08/21/hackers-poison-popular-rust-crates-to-steal-developers-credentials/5291075

著名なRust開発者BurntSushi氏のアカウントが侵害され、arrayref・internment・append-only-vecなど累計2億4500万ダウンロード超のクレートに、ビルド時に不正コードを実行するタイポスクワットパッケージ「proc-macro1」が仕込まれた。Rustプロジェクトは公開から2時間弱で該当バージョンを削除して対応した。
