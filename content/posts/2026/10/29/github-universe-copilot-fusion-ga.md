---
date: "2026-10-29T08:08:19+09:00"
title: "GitHub Universe 2026、複数モデルを自動選択する「Copilot Fusion」をGA——VS Code 1.144にも搭載"
description: "GitHubはGitHub Universe 2026でCopilot FusionのGAやCopilot Projectsなどエージェント時代の開発基盤を発表し、同日のVS Code 1.144にもFusionとComputer Use機能が搭載された。"
tags:
  - OSS
references:
  - "https://github.blog/news-insights/company-news/github-universe-2026-evolving-every-layer-of-the-stack/"
  - "https://code.visualstudio.com/updates/v1_144"
---

## Copilot FusionがGA、複数モデルを自動最適化

GitHubは10月28日、年次カンファレンス「GitHub Universe 2026」において、複数のAIモデルを自動選択・協調させる「Copilot Fusion」の正式提供(GA)を発表した。Fusionは推論、コード生成、デバッグ、ツール使用といったタスクごとの要件を評価し、最適なモデルや実行パターンを自動的に決定するマルチモデルオーケストレーション機能だ。GitHubによれば、Artificial Analysis Coding Agent Indexにおいて「Fusion MaxはOpus 5.5 Maxの2ポイント以内の性能を達成しながら、コストは半額、タスク当たりの所要時間は40%削減」したという。開発者がモデル選択の都度判断を迫られる負担を取り除き、コストと性能のバランスを取ることが狙いだ。

同日公開されたVS Code 1.144にも、このCopilot Fusionが搭載された。VS Code版は、複数モデルを統合する「Project HydraFusion」の技術とCopilotの自動モデル選択機能を組み合わせたもので、モデルピッカーから選択すると、Standard・High・Maxの3段階の推論努力レベルを選べる。複雑なタスクでは複数モデルがドラフト作成・レビュー・批評を分担して協調する仕組みで、応答のホバー表示で実際に使われたモデルを確認できる。有料プランでは2026年11月30日まで30%の利用割引も適用される。

## Copilot Projects・Code Review Maxなどエージェント基盤を拡充

Universe 2026では、Fusion以外にもエージェント時代を見据えた開発基盤が多数発表された。GitHubアプリ上でネイティブに使える「Copilot Projects」は、複数リポジトリをまたいでエージェント作業を実行し、完全管理された並列セッションの進捗追跡や次アクションの指示を一画面で行える。コードレビュー機能「Copilot Code Review Max」は、ベンチマークのReviewBenchで高重大度問題のF1スコア最高値を達成したとされ、従来のLite・Balanced版の高速レビューに加えて、より深い検査を担う。さらにスマートフォンでクラウドエージェントのセッションを開始し、その後VS CodeやCLIから継続操作できる「セッション継続性」や、イベント・スケジュールに応じて自動実行され、結果から学習して改善提案まで行う「Copilot Automations」も発表された。

これらエージェント機能の需要増を支えるため、GitHubはインフラにも大規模投資を行っている。CPU400万コア、高速ストレージ160ペタバイト、ネットワーク容量50Tb/sを追加したほか、Azureでのマルチリージョン展開(2027年初頭の完成を見込む)に加え、ストレージ・コンピュート分離などを原則とする新しいGitアーキテクチャの構築も進めている(完成時期は未発表)。価格体系も見直され、エンタープライズ顧客は個別のCopilot購読なしに全Copilot機能を利用でき、使用したAIクレジット分を支払う方式に転換する。GitHubは「開発者が今日までに書いたソフトウェアは、次の5年間で書くソフトウェアの1%未満となる可能性がある」と述べ、エージェント中心の開発への転換を強く打ち出している。

## VS Code 1.144ではAI画像生成とComputer Useも追加

VS Code 1.144では、Copilot Fusionに加えて2つの新機能が導入された。1つはチャット内でのAI画像生成で、GPT Image 2.5 Flareというモデルを使い、テキストプロンプトからの画像生成や既存画像の編集・変種生成が可能になった。設定`chat.copilot.imageGeneration.model`でモデルを制御し、`off`で無効化できるほか、AI生成であることを示す透明性確保のためウォーターマーク追加オプション(`chat.copilot.imageGeneration.watermark`)も用意されている。

もう1つは実験的機能の「Computer Use」で、チャットで`/computer on`と指示するとエージェントがmacOSやWindowsのデスクトップアプリを視認・操作できるようになる。有効化にはユーザーの承認が必要だが、承認後はCopilotが都度の確認を挟まずに操作を実行する(`/computer off`で無効化可能)。これにより、コードエディタの外側にあるデスクトップアプリの操作やブラウザでの検証作業まで、エージェントによる自動化の対象領域が広がることになる。
