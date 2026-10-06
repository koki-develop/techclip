---
date: "2026-10-06T18:15:12+09:00"
title: "AWSとOpenAIが提携、「Amazon Bedrock Managed Agents」でエージェントをAWS環境内に封じ込める"
description: "AWSはOpenAIのAgents APIをAWSネイティブに統合した「Amazon Bedrock Managed Agents」をパブリックプレビューで公開し、データをAWS環境内に留めたままエージェントを運用できるようにした。"
tags:
  - Cloud
  - AI
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/09/bedrock-managed-agents-preview/"
  - "https://thenextweb.com/news/openai-bedrock-managed-agents-aws-devday"
---

## 概要

AWSは9月29日、OpenAIのAgents APIをAWSネイティブに統合した新サービス「Amazon Bedrock Managed Agents (BMA)」をパブリックプレビューで公開した。AWSとOpenAIの共同開発によるもので、「AWS固有の設計と統合を実現したOpenAI Agents APIのカスタマイズ版」と位置づけられている。最大の特徴はデータの扱いで、推論・メモリ・スキル管理をすべて顧客のAWS環境内で処理し、OpenAIのDevDay 2026で発表された際には「データはAWSを離れず、セキュリティが顧客と次の段階の間の障壁でなくなる」とSalesforceの幹部が述べている。すべての推論はAmazon Bedrock上で実行される。

## 技術的な詳細

BMAはステート管理、ツール選択、コード実行、複数ステップの作業調整を自動的に処理し、永続的なセッションによってメッセージ・ツール呼び出し・中間結果を保持する。Model Context Protocol (MCP) サーバーを含む外部ツールとの接続にも対応する。ガバナンス面では各エージェントに独立したIAMロールと固有のIDを割り当て、重要なアクションの実行前には人間による承認を挟める仕組みを用意。対応するAPI操作はAWS CloudTrailで記録され、監査ログとして残る。実行環境としては、セルフホストの実行環境とAgentCore Runtimeの2つのオプションが選べる。あわせてOpenAIのAgents APIにはコンピューターユース機能も追加され、ブラウザ越しにソフトウェアを操作するエージェントの構築も可能になった。

現在のプレビューはUS East (N. Virginia)、US West (Oregon)、US East (Ohio) の3リージョンで利用可能。料金はプレビュー期間中、基盤となるAWSリソース以外の追加料金はかからないが、本番リリース時には変更される見込みだ。

## 業界への影響

早期採用企業としてSalesforceが紹介されており、自社のデータとコントロール機能をOpenAIのモデルと統合する形で利用している。AWSは、これまでのエージェントのプロトタイプの約90%が市場化に至っていないと指摘しており、BMAをエージェント実装を実用段階に進めるための基盤として位置づけている。クラウド大手とAI企業の提携によるエージェント基盤競争が激化するなか、企業がデータ主権やコンプライアンス上の懸念を抱えたままエージェント技術を導入できる選択肢として注目される。
