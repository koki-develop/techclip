# Zimbraの未認証コマンドインジェクション脆弱性が実悪用、攻撃者がWebシェル設置・認証情報を窃取
Tags: Security

- Attackers Exploit Zimbra Flaw to Deploy Web Shells and Harvest Authentication Secrets (2026-09-30)
  https://thehackernews.com/2026/09/attackers-exploit-zimbra-flaw-to-deploy.html
- Unauthenticated command injection on internet-facing mail servers: tracking CVE-2026-73570 (2026-09-30)
  https://www.microsoft.com/en-us/security/blog/2026/09/30/unauthenticated-command-injection-on-internet-facing-mail-servers-tracking-cve-2026-73570/

Zimbra Collaboration SuiteのSNMP通知機能に存在する未認証コマンドインジェクションの脆弱性(CVE-2026-73570)が実際に悪用されていたことが、Microsoft Threat Intelligenceの調査で判明した。攻撃者はこの脆弱性を突いてJSP形式のWebシェルを設置し、メールボックスのデータや認証情報を窃取していた。インターネットに公開されたメールサーバーが標的となっており、Microsoftは詳細な侵害の経緯と対策を公表している。
