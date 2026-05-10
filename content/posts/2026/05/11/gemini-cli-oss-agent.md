---
date: "2026-05-11T02:24:38+09:00"
title: "GoogleがオープンソースCLI「Gemini CLI」をプレビュー公開、無料で1日1,000リクエスト・100万トークンコンテキスト対応"
description: "GoogleがターミナルからGeminiを直接利用できるオープンソースAIエージェント「Gemini CLI」をプレビュー公開し、個人Googleアカウントで1日1,000リクエストの無料枠と100万トークンのコンテキストウィンドウを提供する。"
tags:
  - AI
  - OSS
references:
  - "https://blog.google/innovation-and-ai/technology/developers-tools/introducing-gemini-cli-open-source-ai-agent/"
---

## 概要

GoogleはオープンソースのターミナルAIエージェント「Gemini CLI」をプレビュー公開した。開発者がコマンドラインから直接Geminiモデルを呼び出せるツールで、自然言語によるコード記述・デバッグ、タスク自動化、Google検索によるリアルタイムな情報との統合などが可能となっている。ライセンスはApache 2.0で、GitHubからインストールできる。

最大の特徴は個人のGoogleアカウントで利用できる無料枠で、1分あたり60リクエスト・1日あたり1,000リクエストまで無償で使える。Googleは「業界最大の無料枠」と位置付けており、プロフェッショナル向けにはGoogle AI Studio APIキー、Vertex AI、Gemini Code Assist Standard/Enterpriseライセンスといった有料オプションも用意されている。

## 技術的な詳細

Gemini CLIはGemini 2.5 Proを基盤としており、100万トークンのコンテキストウィンドウを利用できる。これにより大規模なコードベースやドキュメントをまとめて処理することが可能だ。拡張性の面では、MCP（Model Context Protocol）への対応により既存のエコシステムとの連携も見込まれる。また、`GEMINI.md`ファイルを通じた個人・チーム向けのシステムプロンプトのカスタマイズ機能も備えている。

Gemini CLIはGoogleのIDE向けAIコーディングアシスタント「Gemini Code Assist」と技術基盤を共有しており、VS Code上のGemini Code Assistとも連携できる。すべてのサブスクリプション層（無料・Standard・Enterprise）で追加料金なしにマルチステップのエージェント推論が利用可能とされている。

## 背景と意義

同ツールの登場は、ターミナル上で動作するAIコーディングエージェント市場が活発化している流れに沿ったものだ。Anthropicの「Claude Code」、OpenAIの「Codex CLI」など、各社が開発者の手元の環境に直接AIを組み込むツールを競ってリリースしており、GoogleもGemini CLIでこの競争に加わった形となる。オープンソースで公開することで開発者コミュニティからの貢献を促しつつ、Geminiモデルの採用拡大を狙う戦略と見られる。
