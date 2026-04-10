---
date: "2026-04-10T18:25:29+09:00"
title: "GitHub Copilot に承認不要の完全自律エージェント「Autopilot」モードがプレビュー公開"
description: "VS Code向けGitHub CopilotのMarchリリースで、承認ダイアログを一切挟まずタスク完了まで自律実行する「Autopilot」モードがパブリックプレビューとして導入された。"
tags:
  - AI
  - OSS
references:
  - "https://github.blog/changelog/2026-04-08-github-copilot-in-visual-studio-code-march-releases/"
  - "https://smartscope.blog/en/generative-ai/github-copilot/copilot-cli-autopilot-mode/"
---

## 概要

GitHubは2026年4月8日、VS Code向けGitHub CopilotのMarchリリース（v1.111〜v1.115）を公開し、新たな自律エージェントモード「Autopilot」をパブリックプレビューとして追加した。Autopilotモードでは、ユーザーが一度指示を与えるだけで、Copilotがファイルの編集・テストの実行・エラーの検出と修正をすべて自動で行い、タスク完了まで一切の承認ダイアログを表示しない。従来の「Default Approvals（毎回承認）」「Bypass Approvals（承認スキップ・AIの質問は表示）」に続く第3の権限レベルとして位置づけられており、VS Codeのチャット画面にある権限ピッカーから選択できる。

## Autopilotモードの仕組みと権限レベル

エージェントの動作制御は3段階の権限レベルで管理される。**Default Approvals** はすべてのアクションで承認ダイアログを表示する従来の動作、**Bypass Approvals** は承認ステップをスキップしながらもAIからの質問は表示する中間モード、そして **Autopilot (Preview)** は両方を自動化し、停止条件を満たすまで完全に自律動作する。停止条件はタスク完了、解決不能な問題の検出、ユーザーによる中断（Ctrl+C）、または設定した最大継続ステップ数への到達の4つ。CLI版でも `--autopilot --allow-all` フラグで同様の動作が有効となり、`--max-autopilot-continues` オプションで実行ステップ数の上限を設けることでコスト管理も可能だ。

## 3月リリースで追加されたその他の主要機能

Autopilot以外にも多数の機能強化が含まれる。チャットが画像・動画の入力を受け付けるようになり、エージェントが変更内容を映像で返却できるようになった。新たに統合ブラウザデバッガーが追加され、ブレークポイントの設定やコード実行のステップ追跡、変数のインスペクションをVS Codeを離れることなく行える。サブエージェントが別のサブエージェントを呼び出せるようになり、複雑なタスクの分解にも対応する。また、`#codebase` ツールがセマンティック検索に特化した形で刷新され、ローカル・リモートのインデックス混乱を解消した。さらにモデルピッカーから思考深度を調整できる「Configurable thinking effort」や、カスタムエージェント・スキル・プラグインを一元管理する統合チャットカスタマイズエディタも追加されている。

## 活用場面とコスト管理

Autopilotが特に有効なのは、テストの追加、リファクタリング、CI/CDエラーの修正、バッチコード生成など、明確な完了条件を持つスコープ限定タスクとされている。一方で、各ユーザープロンプトとAIの継続ステップはそれぞれ課金対象となるため、CLI利用時は `--max-autopilot-continues` による上限設定が推奨される。今回のリリースにはTypeScript 6.0サポートやデフォルトテーマの刷新、ローカルHTTPS向け自己署名証明書サポートなども含まれており、VS Code上のCopilot体験が全体的に大きく底上げされている。
