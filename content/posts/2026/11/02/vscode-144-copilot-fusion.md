---
date: "2026-11-02T18:12:14+09:00"
title: "VS Code 1.144リリース、複数AIモデルを自動振り分けする「Copilot Fusion」でエディタをエージェント連携基盤へ"
description: "Microsoftが「VS Code 1.144」を公開し、複数AIモデルを自動オーケストレーションする「Copilot Fusion」やセッション継続用「Agent Host Protocol」、AI画像生成とComputer Use機能を追加した。"
tags:
  - OSS
  - AI
references:
  - "https://code.visualstudio.com/updates/v1_144"
  - "https://visualstudiomagazine.com/articles/2026/10/28/vs-code-1-144-unleashes-copilot-fusion-ai-image-generation-and-computer-use.aspx"
  - "https://www.ntcompatible.com/story/visual-studio-code-1144-ships-microsoft-turns-editor-into-an-ai-agent-command-center"
---

## 概要

Microsoftは開発環境「Visual Studio Code」のバージョン1.144を公開した。最大の目玉は複数のAIモデルを処理内容に応じて自動的にオーケストレーションする「Copilot Fusion」で、エディタをテキスト編集ツールからAIエージェントの操作基盤へと位置づけ直す流れをさらに強めるリリースとなっている。Microsoft自身も「テキストエディタからAIエージェント調整のハブへ」という転換を明確に打ち出しており、有料プランの深掘りとオープンプロトコルによる市場全体の発展という二つの狙いを併せ持つ内容になっている。

## Copilot FusionとAgent Host Protocol

Copilot Fusionは、Project HydraFusionのマルチモデルオーケストレーション技術を基盤とし、リクエストごとに最適なモデル・推論努力レベル・実行パターンを自動選択する機能だ。単純なタスクは単一モデルで完結させ、複雑なタスクではドラフト・レビュー・批評といった役割分担で複数モデルが協調して処理する。ユーザーはStandard・High・Maxの3段階の努力レベルを選ぶだけでよく、同一タスクで複数のAIを競わせて結果を比較する「Agent Bake-Off」機能も搭載された。利用はCopilot Pro+・Max・Business・Enterpriseの各プランで可能で、11月30日までは有料プラン利用時に30%の割引キャンペーンが適用される。

これと対をなすのが、新設されたオープン標準「Agent Host Protocol(AHP)1.0」だ。WebSocketベースで6言語のライブラリが提供され、エージェントのセッションを独立したプロセスで保持したまま、VS Code・Copilotアプリ・GitHub.com・モバイル間でシームレスに引き継げるようにする。Language Server Protocolの設計思想を踏襲した仕組みで、VS Code本体のためだけでなく、サードパーティが独自のエージェントUIを構築するための基盤としても開放されている点が特徴だ。

## AI画像生成とComputer Use

チャット内でのAI画像生成機能も追加され、GPT Image 2.5 Flareを用いて画像の新規生成や既存画像の編集・バリエーション生成が行える。アイコンやワイヤーフレームの作成などに利用でき、生成コストは会話用のAIクレジットに追加で消費される仕組みだ。設定で機能自体をオフにしたり、「Made with AI」ウォーターマークを付加したりすることもできる。

もう一つの注目機能が、実験的な「Computer Use」だ。macOSおよびWindows上のローカルCopilotハーネスセッションに限り、ユーザーが明示的に許可した場合やコマンドで指示した場合に、エージェントがデスクトップアプリを実際に見て操作できるようになる。組織ポリシーによる無効化や`/computer on`・`off`コマンドでの切り替えにも対応しており、安全面への配慮もうかがえる。これに加え、低リスクな呼び出しをLLMが自動評価して承認する「Assisted Permissions」など、権限管理を自動化する仕組みも拡充された。

## 展望

今回のリリース群は、VS Codeを単体のコードエディタとしてではなく、複数のAIモデルやエージェントを横断的に調整する「コマンドセンター」として再定義する狙いが明確だ。Agent Host Protocolのようなオープンプロトコルを公開しつつ、Copilot Fusionでは自社の有料プランへの誘導を図る両面戦略が取られており、今後他社のエディタやツールがAHPに追随するか、またCopilot FusionのようなマルチモデルオーケストレーションがAI支援開発の標準的な体験になっていくかが注目される。
