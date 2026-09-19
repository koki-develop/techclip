# AIコーディングエージェント4製品に影響するゼロクリックRCE脆弱性「Plugin4Shell」が発覚
Tags: Security, AI

- AI coding agents flaw dubbed Plugin4Shell (2026-09-18)
  https://www.helpnetsecurity.com/2026/09/18/plugin4shell-ai-coding-agents-vulnerability/
- Plugin4Shell Lets Repository Owners Swap Pinned Plugin Code Across Four AI Coding Agents (2026-09-18)
  https://thehackernews.com/2026/09/plugin4shell-lets-repository-owners.html
- A zero-click RCE flaw in AI coding agents could have exposed enterprise systems (2026-09-18)
  https://www.infoworld.com/article/4223907/a-zero-click-rce-flaw-in-ai-coding-agents-could-have-exposed-enterprise-systems.html

Claude Code、Codex、GitHub Copilot、Gemini CLIの4製品に共通する脆弱性「Plugin4Shell」が公表された。これらのエージェントはプラグインをコミットハッシュ(SHA)でピン留めして信頼するが、Gitがそのハッシュに対応するコミットの中身を実際には検証しない実装上の欠陥があり、攻撃者はコミットハッシュに似せたブランチ名を使うことで信頼済みのプラグインコードを悪意あるコードにすり替えられる。GitHubはハッシュ状のブランチ名を作成できないため直接的な影響を免れるが、Bitbucketなど他のGitプラットフォームでは危険性が指摘されている。発見元のAir Securityによれば、ユーザー操作なしにコードが実行されるため被害に気づきにくいという。AnthropicのClaude CodeとOpenAIのCodexは既に修正済みだが、MicrosoftのGitHub Copilotは記事執筆時点で未パッチ、GoogleはGemini CLI自体を廃止する対応を取った。
