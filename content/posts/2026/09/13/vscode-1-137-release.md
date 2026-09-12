---
date: "2026-09-13T08:10:23+09:00"
title: "VS Code 1.137リリース、AIエージェントを定期実行する「Automations」とVoice Modeを追加"
description: "VS Code 1.137がリリースされ、AIエージェントをスケジュール実行するAutomations機能や音声で対話できるVoice Modeなど、エージェント活用を広げる新機能が追加された。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://code.visualstudio.com/updates/v1_137"
---

## 概要

Microsoftは9月9日、Visual Studio Codeのバージョン1.137をリリースした。今回の更新は、AIエージェントをより自律的かつ多様な方法で活用できるようにする機能が中心となっている。プレビュー機能として、決まったタスクを定期的にエージェントへ実行させる「Automations」が導入され、実験的機能としては音声でエージェントと対話できる「Voice Mode」、GitHubのIssueやPRをリポジトリを開かずにAgentsウィンドウ内で直接確認できる統合機能なども追加された。

## Automationsによるエージェントタスクの自動化

Automations(設定項目`chat.automations.enabled`)は、変更内容の確認やIssueのトリアージ、バグ検出といった定型的な作業を、手動で都度指示せずにエージェントへ繰り返し実行させる機能だ。時間単位・日単位・週単位のスケジュール実行に加え、オンデマンドでの実行にも対応しており、あらかじめ用意されたテンプレートから目的に合わせたタスクを選べる。利用にはAgentsウィンドウのサイドバーから「Automations」を選択する。現時点ではプレビュー段階にあり、全ユーザーへ段階的に展開されている。

## Voice ModeとGitHub統合

Voice Mode(設定`agents.voice.enabled`など)は、チャット入力欄のボタンから起動し、音声でエージェントに指示を出したり、作業中のエージェントに話しかけて処理を中断・修正したりできる実験的機能だ。エージェントの発話に割り込むほか、プッシュトゥトーク方式での中断も可能で、発話内容のトランスクリプト表示切り替えやマイク選択、音声の変更にも対応する。組織単位でこのプレビュー機能を無効化する管理設定も用意されている。

GitHub連携では、GitHub Pull Requests拡張機能がインストールされていることを前提に、Issueやプルリクエストの詳細をAgentsウィンドウ内で直接確認できるようになった(設定`extensions.experimental.enableAgentsWindowCapability`)。チャットの「Add Context...」メニューからIssueやPRを添付できるほか、URLを貼り付けるだけで自動的にコンテキストとして取り込まれる。Markdownエディタ上のGitHubリンクにもタイトルと状態がライブ表示される機能(`markdown.experimental.richLinks.enabled`)が実験的に追加された。

## その他のアップデートと展望

このほか、ワークスペースを開かずに始めた汎用チャットから、履歴を保持したままプロジェクト固有の作業へ引き継げる機能、複数の差分表示形式(インライン・サイドバイサイド・自動選択)を統一的に切り替えられるSmart diff editor layout、マルチファイル差分での画像などバイナリファイルのプレースホルダー表示、複数エージェントを並列実行するAgent-queued messagesなども追加された。基盤面では、Agent Host Protocol(AHP)に基づく専用プロセスとしてエージェントを実行する「Agent Host」が導入され、Copilot SDKとの統合によって他のCopilot製品との動作統一が図られている。今回の一連の更新は、単発の対話から定期実行・音声操作・外部連携まで、エージェントの活用範囲を広げる方向性を明確に示すものといえる。
