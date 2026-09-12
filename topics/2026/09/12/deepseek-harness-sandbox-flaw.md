# AIコーディングツール「DeepSeek Harness」の脆弱性、AIエージェントが自らのサンドボックスを無効化可能に
Tags: Security, AI

- DeepSeek Harness Flaw Let AI Agents Disable Their Own File Sandbox Without Approval (2026-09-09)
  https://thehackernews.com/2026/09/deepseek-harness-flaw-let-ai-agents.html
- CVE-2026-82533: DeepSeek Harness Vulnerability Lets AI Agents Escape Their Own Sandbox (2026-09-08)
  https://www.ox.security/blog/cve-2026-82533-deepseek-harness-ai-agent-sandbox-escape/
- Flaw in DeepSeek Harness AI Coding Tool Let Agents Disable Their Sandbox (2026-09-09)
  https://devops.com/flaw-in-deepseek-harness-ai-coding-tool-let-agents-disable-their-sandbox/

AIコーディングツール「DeepSeek Harness」に、サンドボックス化されたAIエージェントが認証なしのローカルAPIとHostヘッダーへの過信を突いて自身の権限を「danger-full-access」へ昇格させ、隔離機能を単一のコマンドで無効化できる脆弱性(CVE-2026-82533)が発見された。発見元のOX Securityによれば、リモートの攻撃者が承認なしにエージェントの制御を奪うことも可能だったといい、修正版0.1.2-alpha.1へのアップグレードが呼びかけられている。
