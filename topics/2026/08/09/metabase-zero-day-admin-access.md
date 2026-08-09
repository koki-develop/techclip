# BIツール「Metabase」に未認証で管理者権限を奪える深刻なゼロデイ脆弱性、実際の攻撃でFrameworkの顧客データが流出
Tags: Security

- Metabase Zero-Day Exploited in Wild Allows Admin Access Without Authentication (2026-08-08)
  https://thehackernews.com/2026/08/metabase-zero-day-exploited-in-wild.html
- Metabase SQLi zero-day exploited in customer data-theft attacks (2026-08-07)
  https://www.bleepingcomputer.com/news/security/framework-tally-disclose-metabase-data-theft-attacks/
- Metabase Zero-Day Exploited in the Wild, Exposing Admin Access and Sensitive Data (2026-08-08)
  https://securityaffairs.com/196874/hacking/metabase-zero-day-exploited-in-the-wild-exposing-admin-access-and-sensitive-data.html

BIツール「Metabase」に、未認証のリモート攻撃者がSQLインジェクションを通じて管理者権限を取得できるCVSS 10.0の深刻な脆弱性が発見され、実際の攻撃で悪用されていることが判明した。PCメーカーのFrameworkがこの脆弱性を突かれ顧客データを窃取されたことを確認しており、パスワードリセットAPIを狙う攻撃パターンが報告されている。
