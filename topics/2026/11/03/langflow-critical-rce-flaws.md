# オープンソースのAIエージェント構築ツール「Langflow」に未認証RCEを許す重大な脆弱性
Tags: Security, AI

- Critical Langflow Flaws Could Let Unauthenticated Attackers Run Code on Servers (2026-11-02)
  https://thehackernews.com/2026/11/critical-langflow-flaws-could-let.html
- Langflow OSS: Two Critical 9.8 Flaws Fixed in 1.13.0 (2026-11-02)
  https://aicybr.com/blog/langflow-oss-critical-cves-1-13-0-patch-guide
- Critical Langflow AI Vulnerabilities Allow Hackers to Execute Remote Code Without Authentication (2026-11-03)
  https://gbhackers.com/critical-langflow-ai-vulnerabilities/

オープンソースのAIエージェント構築ツールLangflowに、IBMが発見した複数の重大な脆弱性が公開された。認証バイパス(CVE-2026-93680)と未認証でのリモートコード実行(CVE-2026-110186)の2件はいずれもCVSS 9.8と評価され、回避策はなくバージョン1.0.0〜1.12.8を利用している場合は1.13.0への更新が唯一の対処法とされている。
