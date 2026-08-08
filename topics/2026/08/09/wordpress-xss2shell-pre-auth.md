# WordPressに認証不要のXSSからPHPコード実行に発展しうる脆弱性「XSS2Shell」、早急なパッチ適用を呼びかけ
Tags: Security

- New WordPress Pre-Auth XSS Could Lead to PHP Code Execution - Patch ASAP (2026-08-07)
  https://thehackernews.com/2026/08/new-wordpress-pre-auth-xss-could-lead.html
- New WordPress XSS2Shell: Unauthenticated Login-Screen XSS to PHP Code Execution (CVE-2026-64638) (2026-08-06)
  https://pwn.ai/blog/xss2shell
- WordPress XSS2Shell: Unauthenticated Login-Screen XSS to PHP Code Execution (CVE-2026-64638) (2026-08-07)
  https://hadrian.io/blog/wordpress-xss2shell-unauthenticated-login-screen-xss-to-php-code-execution-cve-2026-64638

WordPressのログイン画面に、認証不要で悪用可能な反射型XSSの脆弱性(CVE-2026-64638、CVSS 8.9、通称「XSS2Shell」)が発見された。管理者権限を持つユーザーが関与する条件下ではPHPコード実行にまで発展する恐れがあり、世界の多数のサイトで使われるWordPressの性質上、影響範囲が広いと懸念されている。脆弱性はWordPress 7.0.3で既に修正済み。
