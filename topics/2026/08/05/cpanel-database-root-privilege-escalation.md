# cPanelに深刻な脆弱性、ホスティング利用者がデータベースのroot権限でSQLを実行可能に
Tags: Security

- New cPanel Critical Flaw Could Let Hosting Customers Run SQL as Database Root (2026-08-04)
  https://thehackernews.com/2026/08/new-cpanel-critical-flaw-could-let.html
- Critical cPanel Vulnerability Allows Execution of SQL Commands as Root User (2026-08-04)
  https://cybersecuritynews.com/cpanel-vulnerability/
- cPanel Database Privilege Escalation Flaw Enables Full Administrative Access (2026-08-04)
  https://gbhackers.com/cpanel-database-privilege-escalation-flaw/

共有ホスティングで広く使われる管理パネル「cPanel & WHM」に、データベースのリネーム処理でSQLモードが保持されない不具合(CVE-2026-58048、CVSS 9.4)が発見された。正規のcPanelアカウントとMySQL/MariaDB機能へのアクセス権を持つ利用者が、データベースのroot権限でSQLコマンドを実行できてしまう恐れがある。
