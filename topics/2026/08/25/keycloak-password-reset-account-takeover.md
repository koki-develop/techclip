# OSS認証基盤Keycloakに重大な脆弱性、未認証でアカウント乗っ取り可能な欠陥が発覚し修正版リリース
Tags: Security, OSS

- Critical Keycloak Password Reset Flaw Could Let Unauthenticated Attackers Take Over Any Account (2026-08-24)
  https://thehackernews.com/2026/08/critical-keycloak-password-reset-flaw.html
- CVE-2026-18963: Keycloak Auth Bypass Vulnerability (2026-08-21)
  https://www.sentinelone.com/vulnerability-database/cve-2026-18963/
- CVE-2026-18963 - Keycloak Credential Reset Authentication Bypass (2026-08-24)
  https://kudelskisecurity.com/research/cve-2026-18963---keycloak-credential-reset-authentication-bypass

オープンソースのID・アクセス管理サーバーKeycloakに、未認証の攻撃者がパスワードリセットフローを悪用して任意のユーザーアカウントを乗っ取れる重大な脆弱性(CVE-2026-18963、CVSS 9.1)が発見された。修正版26.7.2(および26.4.15、26.6.6へのバックポート)がリリースされ、早急なアップデートが呼びかけられている。
