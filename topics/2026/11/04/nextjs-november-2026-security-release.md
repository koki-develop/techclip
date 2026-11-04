# Next.js、テナント間キャッシュ漏洩など7件の脆弱性を修正するセキュリティリリースを公開
Tags: Security, Programming Languages

- November 2026 Security Release (2026-11-03)
  https://nextjs.org/blog/november-2026-security-release
- Next.js security release (Nov 2026): what to know (2026-11-04)
  https://www.netlify.com/changelog/2026-11-03-nextjs-security-vulnerabilities/

Next.jsが、Active LTSのv16.4.5とMaintenance LTSのv15.5.29を対象にセキュリティリリースを公開し、計7件の脆弱性を修正した。中でも重大なのは、Cache Componentsの`use cache`や`unstable_cache`を組み合わせた際に発生するテナント間でのキャッシュ内容漏洩で、他にもEdgeルートでのHttpOnlyクッキー露出やSVGサニタイズ回避なども修正された。Netlifyなどのホスティング事業者も影響範囲と対応手順を案内しており、OpenNextアダプタの更新が必要になるケースもある。
