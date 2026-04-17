---
date: "2026-04-17T18:29:33+09:00"
title: "GoogleがADKのTypeScript版を公開――コードファーストでAIエージェントを構築"
description: "GoogleはAIエージェント構築フレームワーク「Agent Development Kit（ADK）」のTypeScript版をオープンソースとして公開し、TypeScriptエコシステムとの統合や型安全性を強みにマルチエージェント開発を支援する。"
tags:
  - OSS
  - AI
references:
  - "https://developers.googleblog.com/introducing-agent-development-kit-for-typescript-build-ai-agents-with-the-power-of-a-code-first-approach/"
---

## 概要

Googleは2025年12月、AIエージェントおよびマルチエージェントシステムを構築するためのオープンソースフレームワーク「Agent Development Kit（ADK）」のTypeScript版を正式公開した。ADKはもともとPython・Java・Go版が提供されていたが、今回のTypeScript対応により、フロントエンドからバックエンドまで幅広く利用されているJavaScript/TypeScriptエコシステムの開発者もAIエージェント開発に参入しやすくなった。

ADKが掲げるのは「コードファースト」のアプローチだ。エージェントのロジック・ツール・オーケストレーションをTypeScriptで直接定義できるため、複雑なプロンプトエンジニアリングを`Agents`・`Instructions`・`Tools`といったモジュラーでテスト可能なコンポーネントに置き換えることができる。数行のコードで強力なエージェントを定義できる点が特徴とされており、既存のソフトウェア開発プラクティスをAI開発に自然に持ち込める設計となっている。

## 技術的な詳細

ADK TypeScript版の主な特徴は以下の通りだ。

- **エンドツーエンドの型安全性**: TypeScriptの静的型付けを活かし、エージェント定義からツール呼び出しまで型チェックが効く設計
- **TypeScript/JavaScriptエコシステムとの統合**: npmパッケージとして提供され、既存プロジェクトへの導入が容易
- **モジュラー設計**: エージェントやツールを独立したコンポーネントとして定義し、再利用・テストがしやすい構造
- **デプロイメント非依存**: ローカル環境・コンテナ・サーバーレスなど様々な実行環境に対応

対応モデルはGemini 2.5 Flash、Gemini 3 Pro、Gemini 3 Flashをサポートするほか、モデルに依存しない設計のため他社AIモデルとの互換性も維持されている。また、データベースアクセスを容易にする「MCP Toolbox for Databases」とのネイティブ統合も提供され、エンタープライズ用途への適用範囲が広がっている。

## 背景と意義

ADKはGoogleが進めるAI開発の民主化戦略の一環であり、従来のソフトウェア開発プラクティスとAIエージェント開発の融合を目指している。Python版ADKは先行して公開されており、Googleのエコシステム内外で採用が広がっていた。TypeScript版の追加によって、Web開発者を中心とした大規模なコミュニティがマルチエージェントシステム構築に参入できる基盤が整ったことになる。開発者はGitHubリポジトリ・公式ドキュメント・サンプルコードを通じて即座に利用を開始できる。
