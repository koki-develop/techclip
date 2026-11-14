# Apache HTTP Serverに未認証RCEを許す重大な脆弱性(CVE-2026-119618)、AnthropicとGoogleが発見
Tags: Security

- Apache HTTP Server mod_http2 Critical RCE Vulnerability (CVE-2026-119618) (2026-11-11)
  https://www.securityweek.com/apache-patches-critical-http-server-rce-found-by-anthropic-google/
- Apache HTTP Server patches critical HTTP/2 remote code execution flaw (2026-11-12)
  https://www.bleepingcomputer.com/news/security/apache-http-server-patches-critical-http-2-remote-code-execution-flaw/
- Critical Apache HTTP/2 Flaw Could Let Unauthenticated Attackers Execute Code Remotely (2026-11-12)
  https://thehackernews.com/2026/11/critical-apache-http2-flaw-could-let.html

Apache HTTP ServerのHTTP/2モジュール「mod_http2」に、未認証の攻撃者がリモートでコードを実行できる重大な競合状態の脆弱性(CVE-2026-119618、CVSS 9.8)が見つかった。AnthropicのOSSスキャナーとGoogle Cloudの研究者が発見・報告し、修正版2.4.71で対応済み。セキュリティ企業Wizの調査によればクラウド環境の64%に脆弱なリソースが存在するとされ、早急なアップデートが推奨されている。
