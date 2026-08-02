# 人気AIエージェント基盤「Ruflo」にCVSS10.0の最深刻脆弱性「RufRoot」、未認証でコード実行とAIメモリ汚染が可能に
Tags: AI, Security

- Ruflo MCP Flaw Lets Unauthenticated Attackers Run Commands and Poison AI Memory (2026-07-29)
  https://thehackernews.com/2026/07/ruflo-mcp-flaw-lets-unauthenticated.html
- Critical Ruflo flaw lets attackers hijack AI agents through exposed MCP bridge (2026-07-30)
  https://www.csoonline.com/article/4203408/critical-ruflo-flaw-lets-attackers-hijack-ai-agents-through-exposed-mcp-bridge.html
- RufRoot: The MCP Bridge Vulnerability That Turns Agents Into Rogue Admins (2026-07-29)
  https://noma.security/blog/rufroot-the-mcp-bridge-vulnerability-that-turns-agents-into-rogue-admins-cve-2026-59726/

GitHubスターが67,000を超えるオープンソースのAIエージェント基盤「Ruflo」に、認証なしでリモートコード実行、APIキー窃取、AIメモリへの汚染注入が可能な最大深刻度(CVSS 10.0)の脆弱性「RufRoot」(CVE-2026-59726)が発見された。露出したMCPブリッジを悪用することでエージェントを乗っ取り管理者権限を奪えるため、広範なAIエージェント環境への影響が懸念されている。バージョン3.16.3で修正済み。
