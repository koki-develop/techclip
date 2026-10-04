# GitLabのAI Gatewayに重大な脆弱性、セルフホスト環境でコマンド実行が可能に(CVSS9.9)
Tags: Security, OSS

- GitLab Patches Critical 9.9 AI Gateway Flaw Allowing Command Execution on Self-Hosted Servers (2026-10-02)
  https://thehackernews.com/2026/10/gitlab-patches-critical-self-hosted-ai.html
- GitLab warns of critical RCE vulnerability in AI Gateway service (2026-10-02)
  https://www.bleepingcomputer.com/news/security/gitlab-warns-of-critical-rce-vulnerability-in-ai-gateway-service/
- CVE-2026-90970: Critical GitLab AI Gateway Flaw Fixed (2026-10-03)
  https://securityaffairs.com/200283/hacking/cve-2026-90970-critical-gitlab-ai-gateway-flaw-fixed.html

GitLabは、AI Gateway(Duo Agent Platform)に存在するテンプレートサンドボックスエスケープの脆弱性(CVE-2026-90970、CVSS9.9)を修正した。Duo Agent Platformへのアクセス権を持つ認証済みユーザーがサンドボックスを回避し、セルフホストサーバー上で任意のコマンドを実行できる問題で、19.2.4/19.3.2/19.4.1で修正されている。セルフホスト環境の管理者には早急なアップグレードが推奨されている。
