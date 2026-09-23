# Next.jsのImageResponse機能に緊急パッチ、CVSS9.5の重大RCE脆弱性を修正
Tags: Programming Languages, Security

- Next.js Security Update for a Critical Upstream Issue (2026-09-22)
  https://nextjs.org/blog/nextjs-security-update-september-22-2026
- Critical Next.js ImageResponse Flaw Can Lead to Server Code Execution via Crafted SVG Input (2026-09-23)
  https://thehackernews.com/2026/09/critical-nextjs-imageresponse-flaw-can.html
- Next.js ImageResponse security release: what to know (2026-09-22)
  https://www.netlify.com/changelog/2026-09-22-nextjs-imageresponse-vulnerability/

Vercelが開発するReactフレームワークNext.jsのImageResponse機能(next/og)に、細工されたSVG入力によりNode.jsランタイム上でリモートコード実行が可能となる重大な脆弱性CVE-2026-94545(CVSS 9.5)が発見された。9月22日に緊急のセキュリティアップデートとしてv16.3.6およびv15.5.26がリリースされ、Netlifyなどホスティング各社もユーザーに即時アップデートを呼びかけている。
