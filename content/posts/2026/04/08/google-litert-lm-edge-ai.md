---
date: "2026-04-08T02:28:05+09:00"
title: "GoogleがエッジデバイスLLM推論フレームワーク「LiteRT-LM」をOSSとして公開、Chrome・Pixel Watchにも実装"
description: "GoogleはエッジデバイスでのLLM推論に特化したオープンソースフレームワーク「LiteRT-LM」を公開し、Chrome・Chromebook Plus・Pixel Watchにおけるオンデバイス生成AI機能として実装したと発表した。"
tags:
  - AI
references:
  - "https://developers.googleblog.com/on-device-genai-in-chrome-chromebook-plus-and-pixel-watch-with-litert-lm/"
  - "https://aitoolly.com/ai-news/article/2026-04-07-google-launches-litert-lm-a-high-performance-production-grade-framework-for-edge-device-llm-deployme"
---

## 概要

Googleは2026年4月7日、エッジデバイス上でのLLM（大規模言語モデル）推論に特化したオープンソースフレームワーク「LiteRT-LM」を公開した。同フレームワークはgoogle-ai-edgeチームが開発したプロダクション向けの推論エンジンであり、Chrome・Chromebook Plus・Pixel Watchへのオンデバイス生成AI機能としてすでに実装されている。クラウドへの依存を排除することで、ユーザーのプライバシー保護と応答レイテンシの低減を同時に実現する。

## アーキテクチャと技術的最適化

LiteRT-LMはEngine/Sessionパターンを採用している。**Engine**はベースモデルやエンコーダーなどの共有リソースを管理するシングルトンとして機能し、**Session**は個々の会話を担当してステートフルなコンテキストとLoRAウェイトによるタスク固有のカスタマイズを処理する。

メモリと計算効率を最大化するため、以下の3つの主要な最適化機能を備える。

- **コンテキストスイッチング**: タスク切り替え時にKVキャッシュとLoRAの状態を保持し、再計算を省く
- **セッションクローニング**: 計算済みのKVキャッシュ状態をキャッシュし、冗長な処理を回避する
- **Copy-on-Write KVキャッシュ**: バッファを変更が生じるまで共有し、メモリ使用量を最小化する

プラットフォームサポートはAndroid・Linux・macOS・Windows・Raspberry Piに対応し、バックエンドはCPU・GPU・NPUの各ハードウェアアクセラレーターをサポートする。

## 実装事例：Chrome・Chromebook PlusとPixel Watch

ChromeおよびChromebook Plusでは、複数のAI機能が単一のGemini Nanoベースモデルを共有する構成を採用した。これにより、機能ごとに専用モデルを配置する場合と比較してメモリ要件を大幅に削減できる。

Pixel Watchへの実装では、ウェアラブルデバイスの制約に対応するためモジュラー設計が活用された。実行エンジン・トークナイザー・サンプラーという必要最小限のコンポーネントのみを選択して組み合わせることで、限られたリソース内での動作を実現している。この事例はフレームワークの柔軟性と拡張性を示すものだ。

## 開発者向けリソースと今後の展望

LiteRT-LMのC++プレビュー版はGitHub上で公開されており、ドキュメントとサンプルコードも提供されている。対応モデルはLiteRTのHugging Faceコミュニティから参照可能で、エンジンの基礎となるC++インターフェースにも直接アクセスできる。

今回のリリースは、LLM処理の分散化・エッジ化という業界全体の流れを加速させるものとして注目される。クラウドデータセンターへの依存を低減し、よりレスポンシブでプライバシーに配慮したアプリケーション開発を可能にするLiteRT-LMは、エッジAI開発の標準的フレームワークとなる可能性を持つ。
