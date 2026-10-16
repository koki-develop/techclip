# SAP、Cloud SDK for PythonのCVSS10.0のOAuth2 SSRF脆弱性にパッチ公開
Tags: Security

- SAP warns of maximum severity OAuth2 SSRF security flaw (2026-10-13)
  https://www.bleepingcomputer.com/news/security/sap-warns-of-maximum-severity-oauth2-ssrf-security-flaw/
- SAP Discloses Critical CVSS 10 Flaw in Cloud SDK for Python Allowing OAuth2 Credential Theft (2026-10-13)
  https://thehackernews.com/2026/10/sap-discloses-critical-cvss-10-flaw-in.html
- SAP Patches Critical NetWeaver, S/4HANA Vulnerabilities (2026-10-14)
  https://www.securityweek.com/sap-patches-critical-netweaver-s-4hana-vulnerabilities/

SAPは2026年10月のセキュリティパッチデーで、Cloud SDK for PythonにCVSS最大値10.0のOAuth2 SSRF脆弱性(CVE-2026-89111)を含む計20件超のセキュリティノートを公開した。tenant_subdomainパラメータを悪用することでOAuth2のトークンリクエストを攻撃者が制御するサーバーへリダイレクトさせ、クライアント認証情報を窃取できるという欠陥で、NetWeaverやS/4HANAの重大な脆弱性も同時に修正されている。SAPは対象顧客に早急な適用を推奨している。
