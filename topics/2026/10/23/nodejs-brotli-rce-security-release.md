# Node.js、BrotliデコーダのRCE脆弱性含む10件のCVEを修正する緊急セキュリティリリースを公開
Tags: OSS, Security

- Node.js — Wednesday, October 21, 2026 Security Releases (2026-10-21)
  https://nodejs.org/en/blog/vulnerability/october-2026-security-releases
- Node.js Brotli Decoder Bug Could Allow Remote Code Execution in All Supported Versions (2026-10-22)
  https://thehackernews.com/2026/10/nodejs-brotli-decoder-bug-could-allow.html

Node.js 22.x/24.x/26.x系列向けに、合計10件のCVEを修正するセキュリティリリース(22.23.4/24.22.1/26.12.1)が公開された。最も深刻なのはBrotliデコーダのバッファオーバーフローに起因するリモートコード実行の脆弱性(CVE-2026-111497)で、fetch()やExpress 5がBrotliレスポンスを自動展開する仕様のため攻撃対象範囲が広いと指摘されている。全ユーザーに速やかなアップグレードが推奨されている。
