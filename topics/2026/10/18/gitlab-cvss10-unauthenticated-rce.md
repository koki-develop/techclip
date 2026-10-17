# GitLab、CVSS10.0の未認証RCE脆弱性にパッチ公開
Tags: Security

- GitLab Patches CVSS 10.0 Flaw That Could Let Unauthenticated Users Run Server Code (2026-10-13)
  https://thehackernews.com/2026/10/gitlab-patches-cvss-100-flaw-that-could.html
- GitLab warns of max severity code execution vulnerability (2026-10-12)
  https://www.bleepingcomputer.com/news/security/gitlab-warns-of-max-severity-rce-flaw-in-regex-compiler-engine/
- CVE-2026-97229: Critical Unauthenticated Remote Code Execution in GitLab (2026-10-13)
  https://www.rapid7.com/blog/post/etr-cve-2026-97229-critical-unauthenticated-remote-code-execution-in-gitlab/

GitLabはCI/CD用正規表現コンパイラに存在した整数オーバーフロー脆弱性(CVE-2026-97229、CVSS10.0)を修正した。未認証の攻撃者がこの欠陥を悪用し、GitLabサーバー上で任意のコードを実行できる危険性がある。Rapid7の研究者は未パッチのGitLab CE環境で実際に任意コード実行を再現できたと報告しており、広く使われるDevOpsプラットフォームだけに影響範囲の大きさが懸念されている。
