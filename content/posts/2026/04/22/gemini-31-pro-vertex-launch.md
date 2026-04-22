---
date: "2026-04-22T18:29:39+09:00"
title: "Google、Gemini 3.1 ProをVertex AI・Gemini Enterprise・Gemini CLIで提供開始——ARC-AGI-2で77.1%を達成"
description: "GoogleがGemini 3.1 Proを発表し、Vertex AI・Gemini Enterprise・Gemini CLIでのプレビュー提供を開始した。"
tags:
  - AI
references:
  - "https://cloud.google.com/blog/products/ai-machine-learning/gemini-3-1-pro-on-gemini-cli-gemini-enterprise-and-vertex-ai"
---

## 概要

Googleは推論特化モデル「Gemini 3.1 Pro」を発表した。Vertex AI・Gemini Enterprise・Gemini CLIでプレビュー提供が始まり、開発者向けにはGoogle AI Studio・Android Studio・Gemini CLIからもアクセスできる。同モデルはARC-AGI-2ベンチマークで77.1%を達成し、前世代のGemini 3 Proと比べて2倍以上の推論性能を実現している。

## 技術的な詳細

Gemini 3.1 ProはGemini 3シリーズをベースに推論能力を大幅に強化したモデルだ。JetBrainsの社内評価ではGemini 3 Pro Previewと比較して最大15%の性能向上が確認されており、出力トークン数の削減と信頼性向上も同時に達成している。

推論能力の改善は複数の専門領域で顕在化している。3Dアニメーションパイプラインにおけるコード推論（Cartwheel評価）、表形式データと非構造化データを組み合わせたエンタープライズ用途（DatabricksのOfficeQAベンチマークで同クラス最高スコア）、プロンプトの背景にある意図の把握（Hostinger評価）など、複雑なコンテキストを必要とするタスクで特に有効性が示されている。

## 活用事例と評価

早期利用企業からはすでに具体的なフィードバックが寄せられている。JetBrainsは開発者の信頼度向上と問題解決力の改善を報告し、Cartwheelはエッジケースへの対応力と実行精度を高く評価している。Databricksはエンタープライズデータ上でのGenAIアプリケーション構築に適していると述べており、Hostingerはコード品質と意図理解の向上を挙げている。

## 今後の展望

Googleは今回のリリースを「エージェント時代のビジネス変革」を支えるモデルと位置づけており、複数のデータソースを統合して単一ビューで扱う高度なエージェントワークフローへの活用を想定している。現時点ではプレビュー段階であり、正式リリースや価格体系の詳細は今後公表される見込みだ。
