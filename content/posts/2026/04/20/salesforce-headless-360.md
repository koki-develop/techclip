---
date: "2026-04-20T02:17:42+09:00"
title: "SalesforceがAIエージェント時代を見据えた「Headless 360」を発表、全機能をAPI/CLI/MCP経由で提供"
description: "SalesforceはTDX 2026においてGUI不要で全機能をAPI・CLI・MCP経由でアクセスできる「Salesforce Headless 360」を発表し、AIエージェントがSalesforceを直接操作できる環境を実現した。"
tags:
  - Cloud
  - AI
references:
  - "https://www.publickey1.jp/blog/26/salesforceapiclimcpsalesforce_headless_360.html"
---

## 概要

Salesforceは2026年4月15〜16日にサンフランシスコで開催した開発者向けイベント「Salesforce TDX 2026」において、「Salesforce Headless 360」を発表した。これは、従来のWebブラウザUIを介さずに、API・CLI（コマンドライン）・MCP（Model Context Protocol）を通じてSalesforceのあらゆる機能へアクセスできるようにする取り組みだ。Customer 360やData 360、Slackといったサービス群を含むSalesforceプラットフォーム全体が対象となる。

## 背景：AIエージェント時代のUI問題

従来のSalesforceは、WebブラウザによるGUIを中心に設計されており、人間の操作を前提としたインターフェイスが主流だった。しかし、AIエージェントが急速に普及する現在において、こうした人間向けのUIは「むしろ邪魔な存在」になると同社は指摘する。AIエージェントがSalesforceの機能を自律的に活用するためには、機械が直接読み取り・操作できるインターフェイスが不可欠であり、Headless 360はこの課題に正面から応えるものだ。

## 技術的な詳細

Headless 360ではMCPサーバへの対応が盛り込まれており、AIエージェントがMCPを通じてSalesforceの各種機能を呼び出せる。また、コーディングエージェント向けには「Skill for Coding Agents」の提供が開始され、開発ワークフローへの統合が可能になる。さらに、テスト・評価、デプロイ、実験、監視・運用といったアプリケーションのライフサイクル全体をカバーする機能群も提供される。これにより、開発者はGUIを一切使わずにSalesforceプラットフォーム上でアプリケーションを構築・運用できるようになる。

## 将来の展望

Headless 360の発表は、エンタープライズSaaSがAIエージェント時代に向けてアーキテクチャを根本から見直す動きの象徴といえる。人間がUIを操作するのではなく、AIエージェントがプログラマブルなインターフェイスを通じてシステムを制御するモデルへのシフトが加速することで、企業の業務自動化や開発プロセスの効率化が一段と進むと見られる。Salesforceはこの変化をいち早く取り込むことで、エージェント時代のエンタープライズプラットフォームとしての地位確立を狙っている。
