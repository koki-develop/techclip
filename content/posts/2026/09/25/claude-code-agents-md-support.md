---
date: "2026-09-25T18:14:34+09:00"
title: "Claude Codeが「AGENTS.md」に対応、CLAUDE.md不在時に自動読み込みへ"
description: "AnthropicはClaude Code 2.1.277でAGENTS.mdの読み込みに対応し、他のAIコーディングツールとの設定共有が容易になった。"
tags:
  - OSS
references:
  - "https://www.publickey1.jp/blog/26/claude_codeagentsmdclaudemd.html"
---

## 概要

Anthropicは9月18日リリースのClaude Code 2.1.277で、AIコーディングエージェント向け共通仕様「AGENTS.md」の読み込みに対応した。プロジェクトのルートにCLAUDE.mdが存在しない場合、Claude Codeは自動的にAGENTS.mdを参照するようになる。この挙動は「/config」コマンドの「Project instructions」セクションから変更可能で、ユーザーは必要に応じてCLAUDE.mdとAGENTS.mdの優先順位や読み込み方法を調整できる。なお、Amazon Bedrock、Google Vertex、Microsoft Foundry経由の利用では現時点でこの対応が反映されていない。

## AGENTS.mdとは何か

AGENTS.mdは、開発環境のセットアップ手順、テストの実行方法、プルリクエストのガイドラインなど、プロジェクト全体に関わる共通の指示をまとめておくためのMarkdown形式のファイルだ。OpenAI Codex、Google Gemini CLI、Devin、Cursor、GitHub Copilotといった主要なAIコーディングアシスタントの多くはすでにこの仕様をサポートしており、Claude Codeは独自のCLAUDE.mdを採用してきた経緯もあって対応が遅れていた。今回の対応により、Claude CodeもこのAGENTS.mdエコシステムに合流した形になる。

## 背景と今後の影響

複数のAIコーディングツールを併用する開発現場では、これまでツールごとに個別の指示ファイル(CLAUDE.md、AGENTS.mdなど)を用意・管理する必要があり、内容の重複や設定の食い違いが生じやすいという課題があった。今回の対応で、CLAUDE.mdを持たないプロジェクトであればAGENTS.mdひとつで複数ツールの挙動を統一的に制御できるようになる。これは、OpenAI CodexからClaude Codeへ乗り換える場合や、両者を並行して使うチームにとって設定移行・共有のハードルを下げるものであり、AIコーディングツール間での相互運用性がさらに進む動きの一つといえる。
