# PostgreSQLが52件の脆弱性を修正する大規模セキュリティアップデートを公開、バージョン14はEOLに
Tags: OSS

- PostgreSQL 18.7, 17.12, 16.16, 15.20, 14.25, and 19 RC2 Released (2026-11-12)
  https://www.postgresql.org/about/news/postgresql-187-1712-1616-1520-1425-and-19-rc-2-released-3442/
- PostgreSQL security update fixes 52 vulnerabilities, ends support for PostgreSQL 14 (2026-11-13)
  https://www.helpnetsecurity.com/2026/11/13/postgresql-security-update-november-2026/

PostgreSQLグローバル開発グループが18.7、17.12、16.16、15.20、14.25および19 RC2をリリースし、52件のセキュリティ脆弱性と140件以上のバグを修正した。このうち32件のCVEはCVSSスコア8.8の最高深刻度で、PL/PerlやPL/Tclにおけるメモリエラーや型混同に起因するコード実行の問題が中心となっている。過去最大規模の修正となる一方、この更新をもってPostgreSQL 14は公式サポート終了(EOL)となり、本番環境では主要バージョンへの移行計画が必要となる。
