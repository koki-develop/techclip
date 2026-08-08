# Claude CodeとGemini CLIに重大な脆弱性、悪意あるGitHub issueだけでCI環境の認証情報を窃取可能に
Tags: Security, AI

- Claude Code and Gemini CLI Flaws Let a GitHub Issue Reach CI Workflow Secrets (2026-08-07)
  https://thehackernews.com/2026/08/claude-code-and-gemini-cli-flaws-let.html
- Black Hat USA 2026: One GitHub Issue Could Compromise Major AI Coding Workflows (2026-08-06)
  https://hackread.com/black-hat-usa-2026-github-compromise-ai-coding/
- AI coding tools vulnerable to malicious GitHub issues (2026-08-06)
  https://www.scworld.com/brief/ai-coding-tools-vulnerable-to-malicious-github-issues

Black Hat USA 2026でセキュリティ研究者らが、AnthropicのClaude Code(CVE-2026-54316)やGoogleのGemini CLI(CVE-2026-12537、CVSS満点10.0)など主要なAIコーディングエージェントに重大な脆弱性を発見したと発表した。リポジトリへの書き込み権限を持たない第三者が仕込んだ悪意あるGitHub issueだけで、CI実行環境の認証情報を窃取したりコードを実行したりできる恐れがある。
