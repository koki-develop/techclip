---
date: "2026-04-19T18:15:11+09:00"
title: "Eclipse Theia 1.70リリース：AI Coding機能がベータ卒業、Agent ModeがデフォルトでAIファーストIDEへ"
description: "Eclipse Theia 1.70がリリースされ、1年以上ベータ提供されていたAI Coding機能が正式版に昇格。Coder AgentのAgent Modeがデフォルト化され、AI ChatパネルがワークスペースのデフォルトUIに組み込まれた。"
tags:
  - OSS
references:
  - "https://eclipsesource.com/blogs/2026/04/16/eclipse-theia-1-70-release-news-and-noteworthy/"
---

## AI Coding機能がベータを卒業し正式版へ

Eclipse Foundation が開発するオープンソースIDE「Eclipse Theia」のバージョン1.70が2026年4月にリリースされた。最大のハイライトは、1年以上にわたりベータ提供されてきたAI Coding機能群が正式版（GA）に昇格したことだ。IDE固有のAIビュー、Theia Coderエージェント、および関連エージェントがすべて正式サポートとなり、開発者は安心してプロダクション環境での利用を検討できるようになった。

あわせて、デフォルトのワークスペースレイアウトにAI ChatパネルとTerminalパネルが標準で表示されるようになった。これによりAI機能が「オプション」ではなく「常に利用可能なファーストクラスのUI」として位置づけられ、Theiaは名実ともにAIファーストな開発環境へと進化を遂げた。

## Agent ModeがデフォルトになったTheia Coder

AIコーディングアシスタント「Theia Coder」では、従来のEdit Modeに代わり、Agent Modeが新規ユーザーのデフォルトになった。Agent Modeではエージェントがワークスペースのファイルに直接書き込む権限を持ち、より自律的なコーディング支援が可能になる。初回リクエスト時には、Agent Modeがファイルを直接変更できる旨を説明する確認ダイアログが表示され、ユーザーはAgent ModeとEdit Modeのどちらで続けるかを選択できる。安全性への配慮と使いやすさを両立した設計だ。

## 「Capabilities」の強化

1.69で導入された「Capabilities（ケイパビリティ）」が1.70でさらに強化された。Capabilitiesはエージェントの拡張機能を1クリックで有効化できる仕組みで、E2Eテスト実行、シェルアクセス、GitHub連携などの機能を手軽に追加できる。1.70ではCapabilityの設定をsettings.jsonに永続化できるようになり、チームや用途に応じた柔軟な運用がさらに容易になった。

## その他の技術的改善

エディタコンポーネントのMonacoが大幅にアップリフトされ、バージョン1.108に更新された。また、GitHubのCopilotを自動検出する「Copilot auto-discovery」機能も追加され、既存のCopilot環境との統合がよりスムーズになった。今回のリリースでは合計75件のプルリクエストがマージされており、バグ修正やパフォーマンス改善なども含まれる。

Eclipse TheiaはVS Codeと同様にMonacoエディタを基盤とし、クラウドIDEやカスタムツール構築のためのオープンプラットフォームとして広く利用されている。AI機能の正式化により、商用製品やエンタープライズ向けツールへの組み込みがさらに加速することが期待される。
