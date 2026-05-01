---
date: "2026-05-02T02:27:28+09:00"
title: "Visual Studio 2026がIntelliSenseをCopilot補完より優先表示、長年の競合問題をついに解消"
description: "Visual Studio 2026のAprilアップデートで、IntelliSenseとGitHub Copilotの補完候補が同時表示される長年の競合問題が解消され、IntelliSenseが優先される仕様に変更された。"
tags:
  - OSS
references:
  - "https://visualstudiomagazine.com/articles/2026/04/28/visual-studio-2026-gives-intellisense-priority-over-copilot.aspx"
---

## 概要

Microsoftは2026年4月14日にリリースしたVisual Studio 2026 April Update（バージョン18.5）において、IntelliSenseとGitHub Copilotのコード補完が同時表示される問題への対応を実施した。これはGitHub CopilotがVisual Studio 2022に統合されて以来、開発者コミュニティから継続的に報告されてきた問題であり、「エディタが一度に表示する補完候補は1つのみ」という原則に沿う形でIntelliSenseが優先されるよう動作が変更された。Microsoftのリリースノートでは「IntelliSenseとCopilotの補完が同時に表示されると注意が散漫になるというフィードバックを受け取った」と明記されている。

## 問題の背景

GitHub CopilotのVisual Studio統合以降、開発者はキー操作における意図しない競合に悩まされてきた。具体的には「Enterキーでプロパティ名を確定しようとした瞬間にCopilotがIntelliSenseを上書きして不正確な補完候補を提示する」「TabキーをどちらのシステムPが処理するのか判別できない」といった問題がGitHub Communityのディスカッション（Discussion #15649など）で数年にわたって議論されてきた。複数の補完システムが同時に介入することで、開発者のフロー状態が頻繁に中断されていた。

## 技術的な変更内容

今回の変更では、IntelliSenseが有効な状態の間はCopilotのインライン補完が一時的に抑制される仕組みが導入された。IntelliSenseのリストで補完を確定または却下した後、CopilotによるAI補完が自動的に再開される。この優先順位付けはデフォルトで有効となっており、ユーザーが追加の設定変更を行わなくても恩恵を受けられる。4月21日にリリースされたバージョン18.5.1でも引き続き同動作が維持されている。

## 今後の展望

同時期のアップデートでは、バックグラウンドでタスクを実行しPull Requestの作成まで自動で行うCloud Agent統合、デバッグ作業を支援するDebugger Agent、過去の会話を管理するChat Historyパネルなど、より高度なAIエージェント機能も追加された。Visual StudioへのAI統合は単なるコード補完にとどまらず、開発ワークフロー全体を自動化する方向へ継続的に拡張されており、今回のIntelliSense優先対応はその基盤となるエディタ体験の整備という位置付けでもある。
