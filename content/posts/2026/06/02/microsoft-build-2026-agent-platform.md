---
date: "2026-06-02T03:58:00+09:00"
title: "Microsoft Build 2026：WindowsをAIエージェント基盤に再定義、Project PolarisでOpenAI依存を脱却"
description: "Microsoft Build 2026でWindowsが3層構造のAIエージェントプラットフォームとして再定義され、自社開発モデル「Project Polaris」によるGitHub Copilotのエンジン刷新など開発者向け大型発表が相次いだ。"
tags:
  - AI
  - Programming Languages
references:
  - "https://chatforest.com/builders-log/microsoft-build-2026-recap-windows-agent-platform-project-polaris-copilot-workspace/"
  - "https://faq.com.tw/en/developer-tools/2026-05-27-microsoft-build-2026-sf-agents-azure-ai-foundry-en/"
---

## 概要

Microsoft Build 2026が6月2〜3日にサンフランシスコのフォートメイソンで開幕し、Microsoftは「Windowsをエージェントプラットフォームとして再定義する」という方針のもと、開発者向けの大型発表を相次いで行った。約2,500人規模の開発者イベントとして設計された今回のカンファレンスでは、AIエージェントが中心テーマに据えられ、エンタープライズ展開から本番運用フェーズへの移行を加速する施策が打ち出された。

最大のサプライズは**Project Polaris**の発表だ。MicrosoftがGitHub Copilotのデフォルトエンジンとして採用しているGPT-4 Turboを自社開発モデルに置き換えるプロジェクトで、2026年8月より切り替えが始まる。Mixture-of-Experts（MoE）アーキテクチャを採用した同モデルは、HumanEvalおよびMBPPベンチマークでGPT-4 Turboを上回るとされ、特に低リソース言語での性能が強みとして挙げられた。この移行によりMicrosoftはモデル・推論インフラ・開発者体験の全てを自社コントロール下に置くことになる。

## Windows AIエージェントプラットフォームの構造

Windowsのエージェント基盤は以下の3層アーキテクチャで構成される。

**Windows Agent Framework（WAF）v1.0**はMITライセンスで公開される開発者向けSDKで、YAMLでエージェントを定義すればローカルマシンからWindows 365 Cloud PC、Azure Arcエッジデバイスまでアーキテクチャの変更なしにスケールできる。**Windows Agent Runtime**はOSレベルのネイティブAPIを提供し、エージェントをファーストクラスの存在として扱う。現在のプレビューではJSON・XML・PDFファイルに対するテキストベースのエージェントをサポートしており、AdobeやZoomなどがパートナーとして参加している。**Windows Agent Store**はキュレーションされたエージェントのマーケットプレイスで、収益の85%が開発者に配分される——これは現行のMicrosoft Storeと同条件だ。

インフラ面では、オンプレミス・クラウド・エッジにまたがる実行を統合する**Azure Agent Mesh**（2026年Q4 GA予定）、Intel・AMD・Qualcomm NPUの差異を吸収してクラウドラウンドトリップなしにローカルAI推論を可能にする**DirectML 2.0**、GPU/NPUアクセス付きでLinuxカーネルを仮想化する**WSL 3**も発表された。

## GitHub CopilotとAzure AI Foundryの強化

GitHub Copilot/Copilot Workspaceがベータを卒業し、正式リリースとなった。Jira・Datadog・ServiceNowとの拡張機能連携、自律的な反復タスクを処理する「フリートモード」、スケジュール実行でバックグラウンド操作を行う「オートパイロット」機能が追加されている。またCopilotはマルチモデル対応にシフトし、OpenAIモデルに加えてAnthropicのClaudeも代替として選択できるようになる。

.NETおよびPython向けの**Agent Framework 1.0**も本番提供が開始された。階層的なエージェント調整、イベント駆動型ワークフロー、ステートフルなエージェント機能をサポートする。Azure AI Foundryのモデルカタログは約1,600から3,000以上に拡張され、エージェント評価ツールとDevUIデバッガーも追加された。

## マルチモーダルモデルMAI v2

Microsoftは自社のマルチモーダルモデルスイート「MAI v2」も発表した。画像生成・編集機能を持つ**MAI-Image-2.5**、14言語・感情表現に対応した**MAI-Voice-2**、前バージョンMAI-Transcribe-1が25言語で単語誤り率3.9%（FLEURS）を達成しており、その漸進的な改良版である**MAI-Transcribe-1.5**の3モデルで構成される。価格設定は一般提供時に公表される予定だ。

今回のBuild 2026は、MicrosoftがAzure AI収益の拡大を背景に、単なるAIモデルの提供者からエンドツーエンドのエージェント実行基盤へと自社を再定位する戦略的転換点と言える。Project PolarisによるOpenAI依存の低減は、同社のAI事業における長期的な独自性確保という観点でも注目される。
