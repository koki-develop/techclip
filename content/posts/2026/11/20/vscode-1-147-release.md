---
date: "2026-11-20T18:09:22+09:00"
title: "VS Code 1.147リリース、AIエージェントが実ブラウザを操作する「Browser Use」とチャット予約送信「Send Later」を追加"
description: "Visual Studio Code 1.147が公開され、AIエージェントが既存ブラウザを直接操作する「Browser Use」や、チャットリクエストを予約送信する「Send Later」など複数の実験的機能が追加された。"
tags:
  - OSS
references:
  - "https://code.visualstudio.com/updates/v1_147"
  - "https://github.com/microsoft/vscode-docs/blob/main/release-notes/v1_147.md"
---

## 概要

Microsoftは11月18日、Visual Studio Codeの最新安定版1.147をリリースした。最大の注目点は、AIエージェントがVS Codeの外にある実際のブラウザ(Google ChromeやMicrosoft Edge)を直接操作できる「Browser Use」機能で、現在プレビュー公開されている。これに加え、チャットリクエストの送信時刻を予約できる「Send Later」、作業内容に応じて使用モデルを自動で振り分ける「Model Router」、複数の未送信リクエストを並行管理できる「ドラフト」機能など、エージェント関連の実験的機能が一挙に追加された。

## Browser Useでエージェントが実ブラウザを操作

Browser Useは、`chat.agentHost.browserUse.enabled`設定を有効にしてVS Codeを再起動し、ローカルのCopilot harnessセッションで「`/plugin enable browser-use`」コマンドを実行することで利用できる。利用にはGitHub Copilotブラウザ拡張機能とNode.js 22以上が必要で、動作確認用に「`/browser-use:doctor`」コマンドも用意されている。

有効化後は、「`Open my app at localhost:3000, check the navigation, and capture a screenshot.`」のように自然言語でタスクを指示するだけで、エージェントが実際のブラウザを開いて操作する。ポイントは、ユーザーが普段使っているブラウザの既存の認証セッションをそのまま再利用できる点で、ログインが必要なサイトでの検証作業も、手動でログインを済ませておけばエージェントに引き継がせられる。サイトへのアクセスはユーザーの承認が必要なため、セキュリティ面への配慮もなされている。

## Send Later・ドラフト・Model Routerで広がるエージェント運用

Send Laterは実験的機能で、チャット送信ボタンのメニューから「Send Later」を選び、プリセット時間やカレンダーから送信時刻を指定できる。「`Check the build in 10 minutes.`」のように自然言語で予約することも可能だが、マシンがスリープしていると動作しない点には注意が必要だ。ローカルのAgent Hostでの実行かつ自動化の有効化が前提条件となる。新規セッションで予約した場合はドラフトセクションに、既存チャットの場合はスケジュール済みエリアに表示され、他のエージェントが実行中であれば待機キューに並ぶ仕組みだ。

同時に追加されたドラフト機能(実験版)は、複数の未送信リクエストをそれぞれ独立したワークスペース・エージェント・モデル設定を保持したまま保存できる。VS Codeを再起動してもドラフトは失われない。さらにModel Router機能(実験版)では、`~/.agents/model-routers/`に置いたYAMLファイルでタスクの種類ごとに使用モデルを割り当てられる。たとえば複数ステップにわたるコード変更にはOpus系モデル、簡潔な質問には軽量な「`gpt-6-luna`」系モデルを割り当てる、といった設定が例として挙げられている(ルーティングの判定自体は決定モデル「`gpt-6-luna-decisions`」が行う)。この他、HTMLプレビューやネイティブビジュアル(グラフ・表の直接レンダリング)、Markdownテーブルのセル単位編集、`<details>`タグの折りたたみ表示対応など、エディタ体験の細部にも改善が加えられている。

## Enterprise向けの変更と非推奨化

企業向けには、管理設定の`vscode.allowedHarnesses`に`["claude", "codex"]`のように列挙することで、GitHub Copilotのガバナンスを維持したままClaudeやCodexといった他のAIハーネスを併用できるようになった(空リストにすると両方がブロックされる)。ただし現時点ではファイルベースやMDMによる管理設定のみが対象で、サーバー管理設定はまだ対応していない。またCopilot harnessセッションのシェル権限ルール(`Shell()`、`Bash()`、`PowerShell()`)が正規表現に対応し、「`Shell(/^git\s+(push|pull)\b/)`」のような柔軟なルール記述が可能になった。

一方で、Local harnessは2027年2月に廃止予定となり、macOS Ventura・Sonomaおよび32-bit ARM Linux向けのデスクトップサポートも非推奨(deprecated)となった(これら2件については具体的な終了日は明示されていない)。AI使用統計の表示機能(`editor.aiStats.enabled`)も本バージョンで削除された。Browser UseやSend Later、Model Routerはいずれも実験的・プレビュー機能であり、今後のフィードバックを受けて仕様が変わる可能性がある。VS CodeがAIエージェントの「実行環境」としての役割を拡張し続ける方向性が、今回のリリースでも明確に示された。
