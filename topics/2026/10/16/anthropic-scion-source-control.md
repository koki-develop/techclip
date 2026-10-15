# Anthropic、Gitに代わる自社製バージョン管理システム「Scion」を開発
Tags: AI

- Redesigning Source Control at Anthropic (2026-10-13)
  https://www.anthropic.com/engineering/redesigning-source-control
- Anthropic reinvents source control as Claude floods the world with code (2026-10-13)
  https://www.theregister.com/devops/2026/10/13/anthropic-reinvents-source-control-as-claude-floods-the-world-with-code/5302943

AnthropicはClaudeによるコード生成量が5月の1日2,500件から9月には3万件超に急増したことを受け、既存のGitでは対応が難しくなったとして、独自のバージョン管理システム「Scion」を開発した。AIエージェントによる大量かつ高頻度のコード生成・変更に最適化するため、サーバー主体でAPI経由のクエリに特化した集中型モノレポ方式を採用し、分散型のGitとは異なるアーキテクチャを公開した。
