---
date: "2026-05-15T02:39:39+09:00"
title: "Red HatがAIエージェント向けスキルリポジトリを公開、20年分のインフラ運用知識をオープンソースで提供"
description: "Red Hat Summit 2026にてRed HatはRHEL・OpenShift・Ansibleに関する20年分のベストプラクティスをエンコードしたオープンソースのアジェンティックスキルリポジトリを発表し、Claude CodeやCursorなど主要AIコーディングエージェントから利用できるようにした。"
tags:
  - OSS
  - AI
references:
  - "https://www.businesswire.com/news/home/20260512950588/en/Red-Hat-Launches-New-Developer-Tools-for-Agentic-AI"
  - "https://thenewstack.io/red-hat-agentic-skills-repository/"
---

## 概要

2026年5月12日にアトランタで開催されたRed Hat Summitにて、Red HatはAIエージェント向けの「Agentic Skills Repository（アジェンティックスキルリポジトリ）」を正式発表した。このリポジトリは、RHEL・OpenShift・Ansibleの運用を通じて蓄積された20年分の企業インフラ知識をスキルパックとしてエンコードしたもので、GitHubのオープンソースリポジトリ（`openshift/agentic-skills`、Apache 2.0ライセンス）として公開されている。Claude Code、Cursor、Windsurf、OpenShift Dev Spacesなど主要なAIコーディングアシスタントから利用可能で、Red Hat AI最新リリースに追加費用なしで含まれる。

CEO Matt Hicksは「モデルはAIのエンジンとよく語られるが、エンタープライズの文脈では特定のスキルを持たないモデルはハンドルのない高性能車のようなものだ」と述べ、汎用LLMの大規模化では補えない特定ドメインの運用知識こそが差別化要因であると強調した。The New Stackの記事タイトルが「a bigger model never could」と表現したように、どれだけ大きなモデルでも持ち得ない企業固有の蓄積知識をスキルパックとして流通させる新しいモデルを提示している。

## 利用可能なスキルパック

現在リリースされている主なスキルパックは以下の通りだ。

- **Agentic Skill Pack for Red Hat OpenShift**：OpenShiftクラスターのプロビジョニング、インベントリ、レポートを会話型ワークフローで実施。Assisted Installer、OCM、ROSA、AROなど複数のデプロイ方式とkubeconfigフリートをまたいで管理できるDeveloper Previewのスキル。
- **Agentic Skill Pack for Red Hat OpenShift Virtualization**：OpenShift仮想化環境に特化した操作スキル。
- **CVE Explainer**：Red HatのCVEデータベースやセキュリティアドバイザリAPIにリアルタイムで接続し、特定CVEの深刻度評価と環境固有の対応推奨を提供する。
- **Diagnostic Data Gathering**：sosreport、must-gather、Ansibleの診断バンドル収集を段階的に案内するスキル。
- **Product Lifecycle Advisor**：Red Hat製品・バージョンのサポートフェーズとアップグレードタイムラインを明示する。
- **Support Severity Helper**：サポートケースの適切な深刻度レベルを判定し、SLAと必要情報を説明する。

各スキルパックはポータブルで、バージョン管理された検査可能なソフトウェアとして設計されており、ベンダーロックインのプロンプトではなく開かれた形式で提供されている点が特徴だ。

## 技術的なアーキテクチャ

スキルパックは、`agentskills.io`のオープンフォーマット、Claude Skills形式、OpenAI Skills形式の3種類のオープン規格をサポートし、主要なAIコーディングアシスタントとの相互運用性を確保している。実装言語はPython（77.3%）とShell（22.4%）が中心で、スキルはコンテナ化されており`Containerfile`でビルドしてイメージボリュームとしてマウントする方式を採る。

MCP（Model Context Protocol）との統合も重要な要素で、エージェントはMCPサーバーを通じてカスタム統合なしに外部システムと連携できる。Red Hat AI・OpenShift AIはLlama StackとMCPの統合を提供しており、Red Hat AI Inference ServerとClaude Codeを組み合わせるチュートリアルも公開済みだ。スキルのインストール・管理にはパッケージマネージャー「Lola」を使用する。

## Red Hat Summitの関連発表

スキルリポジトリ発表と同時に、Red Hatは複数の開発者向けツールを発表・強化した。Red Hat Desktop（GA）は商用サポート付きのPodman Desktopで、「Isolated AI Agent Sandboxing」によってAIエージェントをホストOSから隔離した環境でテストできる。OpenShift Dev SpacesではAWS Kiro（テクニカルプレビュー）への統合が拡張され、既存のMicrosoft Copilot、Claude CLI、Cline、Continue、Rooなどと並んでクラウドIDEから利用できる。Red Hat AI 3.4では、vLLMによるSpeculative Decodingを導入してレスポンス速度を2〜3倍向上させるとともに、モデルのガバナンス管理やMCPゲートウェイのサポートが追加された。

CTO Chris Wrightはフロンティアモデルのトークン単価が年間75〜90%低下する一方、推論モデルが標準モデルの10〜20倍のトークンを消費し、エージェントはさらに5倍の乗数を加えると指摘し、APIを消費するのではなく推論インフラを自社保有する経済合理性を強調した。Red Hatは「既存インフラにエージェントを重ねる」という戦略で、プラットフォーム移行を前提とするハイパースケーラー勢との差別化を図っている。現在、GitHubリポジトリはまだ成長段階にあるが、Claude CodeやCursorを日常的に使うRed Hat環境の開発者・管理者にとってすぐに試せる実用的なエコシステムが整いつつある。