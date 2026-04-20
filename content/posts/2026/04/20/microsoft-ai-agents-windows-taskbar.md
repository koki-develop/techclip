---
date: "2026-04-20T10:38:40+09:00"
title: "MicrosoftがWindows 11タスクバーへのAIエージェント統合を正式確認、MCPでサードパーティにも開放"
description: "MicrosoftはWindows 11のタスクバーにAIエージェントを統合する計画を正式に確認し、Model Context Protocolを通じてサードパーティ開発者がエージェントを接続できる仕組みも整備しつつある。"
tags:
  - AI
references:
  - "https://www.windowslatest.com/2026/04/18/microsoft-confirms-ai-agents-are-still-coming-to-the-windows-11-taskbar-as-it-prepares-for-public-rollout/"
  - "https://wccftech.com/microsoft-continues-with-its-plan-to-bring-ai-agents-to-windows-11/"
---

## 概要

Microsoftは、Windows 11のタスクバーにAIエージェント機能を統合する計画を正式に確認した。同社が一部のアプリからCopilotを削除したことで「AI縮小路線」への転換と受け取られる向きもあったが、今回の発表はそうした憶測を否定するものだ。スニッピングツールや写真アプリなど実用性が低い文脈からCopilotを取り除いている一方で、タスクバーへのエージェント統合は引き続き推進しており、「AIをより意図的に、価値を発揮できる場所に絞り込んでいる」というのがMicrosoftの立場だ。パブリックロールアウトに向けた準備が進められており、段階的なオプトイン方式での提供が予定されている。

## 技術的な詳細

AIエージェントは「計画し、調査し、推論し、ユーザーの介入なしに実行する」自律型システムとして設計されている。ユーザーはタスクバー上のMicrosoft 365 Copilotアイコンにホバーすることで、エージェントの動作をモニタリングしたり制御したりすることができる。

現時点で最初にサポートされるエージェントは**Microsoft 365 Researcher**だ。OneDriveやMicrosoft 365のファイルにアクセスしながら複数ステップにわたる調査タスクを実行し、詳細なレポートをタスクバーから直接生成する機能を持つ。開発者向けには**Model Context Protocol（MCP）**を採用しており、サードパーティ開発者が互換性のあるエージェントを構築してタスクバーに接続できる仕組みが整備されている。さらに深いOSレベルの統合が必要な場合は**Windows.UI.Shell.Tasks API**も利用可能だ。

## 利用条件と今後の展望

この機能の利用にはMicrosoft 365サブスクリプションが必要であり、自動的に有効化されるものではなく完全なオプトイン方式となっている。現状のサポートはMicrosoft 365アプリに限定されているが、MCPを通じたサードパーティ製エージェントの参入により、将来的には対応するエージェントの幅が大きく広がると見られる。Windowsのタスクバーという常時アクセス可能な場所にAIエージェントが常駐することで、デスクトップ上でのAI活用がより日常的になる可能性がある。
