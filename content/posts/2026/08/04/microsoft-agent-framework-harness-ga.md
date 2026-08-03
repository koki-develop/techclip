---
date: "2026-08-04T02:31:34+09:00"
title: "Microsoft Agent Framework、「Agent Harness」とHosted Agentsが正式GAへ ― Claude Agent SDKとも直結"
description: "Microsoft Agent Frameworkの実行基盤「Agent Harness」とFoundry Hosted Agentsが正式GAとなり、GitHub Copilot SDKやClaude Agent SDKとの直接連携、順次・並列・Magenticのマルチエージェント編成パターンが安定版として利用可能になった。"
tags:
  - AI
  - Programming Languages
references:
  - "https://www.infoq.com/news/2026/08/agent-framework-harness-ga/"
---

## 概要

Microsoftは、2025年10月にSemantic KernelとAutoGenを統合するオープンソースプロジェクトとして立ち上げた「Microsoft Agent Framework」について、2026年4月2日に1.0を正式リリースしていたが、続く6月2〜3日開催のBuild 2026で発表した実行基盤「Agent Harness」、GitHub Copilot SDKおよびClaude Agent SDKとの連携コネクタ、そしてマルチエージェント編成パターン群が、このたび正式GA(General Availability)に到達した。あわせて、Agent Framework向けのマネージドなホスティング環境である「Foundry Hosted Agents」も正式提供が始まっている。MicrosoftのプリンシパルソフトウェアエンジニアであるWes Steyn氏は「モデル単体はテキストを生成するだけの存在だ」と述べ、harnessが単なるモデル呼び出しの薄いラッパーではなく、実運用に耐える実行環境そのものを提供する点を強調している。

## Agent Harnessの技術的な詳細

Agent Harnessは、ローカル開発環境・コンテナ・ホスティング環境のいずれでも単一バイナリとして動作する、本番運用を想定したランタイムである。関数呼び出し(function invocation)、会話履歴の永続化、コンテキスト圧縮、plan/executeモードを備えたTODOリスト管理、ファイルメモリ、スキル(skills)、Web検索、ツール承認(tool approval)、そしてOpenTelemetryによる可観測性を標準機能として内蔵する。また、エージェントが意図せず無限ループに陥ることを防ぐ「暴走ループ防止」機構も備える。多くの機能はデフォルトで有効になっている一方、シェル操作やファイルアクセス、バックグラウンドのサブエージェント、自動的なループ実行といった強い権限を伴う機能はオプトイン扱いとされ、有効化時には警告が表示される設計になっている。

GitHub Copilot SDKおよびClaude Agent SDKとのコネクタは、カスタムアダプタを介さずに直接統合できる点が特徴で、既存のID管理・コンテンツセーフティ・可観測性のポリシーをそのまま適用しつつ、コーディングエージェントのトラフィックを既存のOpenTelemetryトレーシング基盤に統合できる。マルチエージェント編成については、線形にタスクを処理する「順次パイプライン」、複数エージェントが同時に作業する「並列協調」、そしてMicrosoft ResearchのMagentic-One(2024年発表、GAIAベンチマークで38%、AssistantBenchで27.7%、WebArenaで32.8%のスコアを記録)に由来する「Magenticパターン」の3種類が単一のAPIの下で安定版として利用可能になり、実装を切り替えることなく編成方式を変更できる。

## ベンチマークと業界の議論

MicrosoftのAIプリンシパルアーキテクトであるAqib Sherwani氏は、Agent FrameworkとGitHub Copilot SDKを比較するベンチマークを実施し、「同じ推論能力だが、エンジニアリングが異なる」と結論づけた。同氏の検証では、Agent Frameworkは40回のラウンドトリップで自律ループを停止させたのに対し、ホスト側の制御を無効化したGitHub Copilot SDKは300回まで停止せずに実行を続けたという。

こうしたharnessの重要性は、外部の研究によっても裏付けられている。MBZUAIのVILA-Labが2026年4月に発表した分析「Dive into Claude Code」では、2026年3月31日に流出したClaude Code v2.1.88のソースマップ(約512,000行、1,884ファイル)を行数ベースで分類したところ、コードベースの98.4%がharnessのインフラストラクチャや権限管理、コンテキスト処理に費やされており、AIの意思決定ロジックそのものはわずか1.6%に過ぎなかったという(著者らは、これがミニファイされた流出バンドルを行数で分類した結果である点に注意を促している)。この結果は、優れたエージェント体験の実現においてモデル自体よりも周辺のエンジニアリングが大きな比重を占めるという、業界全体の潮流を象徴する数字として引用されている。

## 今後の展望

Agent Frameworkは.NETとPython向けにGitHub上で公開されており、Foundry Hosted Agentsは従量課金制のマネージドホスティングとして提供される。GitHub Copilot SDKやClaude Agent SDKとの直接統合が正式にサポートされたことで、開発者は既存のコーディングエージェントのワークフローに、Microsoftのharnessが提供する運用機能(観測性、権限管理、暴走防止など)をそのまま組み込めるようになる。一方で、Sherwani氏のベンチマークが示すように、暴走ループ防止の挙動はSDKごとに大きく異なっており、複数のエージェントSDKを併用する開発者にとっては、それぞれのデフォルト挙動や安全機構の違いを理解した上で採用する必要がありそうだ。
