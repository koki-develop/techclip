# 研究者、Webサイト要約の指示だけでClaude Code Auto Modeを突破する攻撃を実証
Tags: AI, Security

- Researcher shows how Claude Code can be tricked simply by asking it to summarize a website (2026-08-28)
  https://www.theregister.com/research/2026/08/28/researcher-shows-how-claude-code-can-be-tricked-simply-by-asking-it-to-summarize-a-website/5293372
- Hidden Attack Slips Past Claude Code Auto Mode (2026-08-28)
  https://www.govinfosecurity.com/hidden-attack-slips-past-claude-code-auto-mode-a-32693
- A Simple Website Summary Just Exposed the Limits of AI Coding Guardrails (2026-08-31)
  https://devops.com/a-simple-website-summary-just-exposed-the-limits-of-ai-coding-guardrails/

セキュリティ研究者Johann Rehbergerが、AnthropicのClaude Code(Opus 5、Auto Modeがデフォルト)に対しウェブサイトの要約を依頼するだけでコードを実行させるプロンプトインジェクション攻撃を実証した。悪意あるサイトがZIPアーカイブをダウンロードさせ、Python標準ライブラリを装った悪意のあるstruct.pyを読み込ませる手法で、60〜80%の確率で成功するという。Anthropicはこの報告を「informative」として重大な欠陥とは扱わず、Auto Modeの承認分類器はあくまで「best-effort」であり真のセキュリティ保証ではないとの見解を示している。
