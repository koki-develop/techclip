# Node.jsがHTTP/2・TLS関連を含む16件の脆弱性を修正するセキュリティリリースを公開
Tags: OSS, Security

- 2026 November Security Releases (2026-11-11)
  https://nodejs.org/en/blog/vulnerability/november-2026-security-releases
- Node.js Fixes 16 Flaws, Including HTTP/2 Bugs That Crash Servers and Leak Other Connections' Data (2026-11-12)
  https://thehackernews.com/2026/11/nodejs-fixes-16-flaws-including-http2.html

Node.js v22.23.5、v24.22.3、v26.13.1が公開され、16件の脆弱性(深刻度「高」7件を含む)が修正された。HTTP/2関連でサーバーがクラッシュする問題や、HTTPS経由で別の接続のTLS秘密鍵・リクエスト内容が漏洩する問題などが含まれ、全ユーザーへの早急な更新が推奨されている。
