---
date: "2026-03-29"
title: "Kubernetes上のLLM推論を革新する「llm-d」がCNCF Sandboxプロジェクトに採択"
description: "Red Hat・Google・IBM・CoreWeave・NVIDIAが共同開発したKubernetesネイティブの分散推論フレームワーク「llm-d」がCNCF Sandboxプロジェクトとして正式に採択された。"
tags:
  - Cloud
  - AI
references:
  - "https://www.cncf.io/blog/2026/03/24/welcome-llm-d-to-the-cncf-evolving-kubernetes-into-sota-ai-infrastructure/"
  - "https://thenewstack.io/llm-d-cncf-kubernetes-inference/"
  - "https://siliconangle.com/2026/03/24/red-hat-bets-big-kubernetes-inference-llm-d-kubeconeu/"
---

## 概要

KubeCon Europe 2026にて、Kubernetes上でLLM推論を最適化する分散推論フレームワーク「llm-d」がCNCF Sandboxプロジェクトとして採択された。llm-dは2025年5月にRed Hat、Google Cloud、IBM Research、CoreWeave、NVIDIAによって立ち上げられたプロジェクトで、AMD、Cisco、Hugging Face、Intel、Lambda、Mistral AI、UCバークレー、シカゴ大学など幅広い企業・研究機関が支援している。KServeのような高レベルのコントロールプレーンとvLLMのような低レベルの推論エンジンの間を橋渡しし、ハードウェアベンダーに依存しない「あらゆるアクセラレータ上でのSoTA推論性能」の実現を目指している。

## アーキテクチャと技術的特徴

llm-dの中核となる技術革新は「Disaggregated Serving（分離型サービング）」だ。LLM推論のprefill（入力処理）フェーズとdecode（トークン生成）フェーズを独立したスケーラブルなPodに分離することで、リソース配分とレイテンシ管理をきめ細かく制御できるようにしている。Red HatのAI CTO Brian Stevens氏は「分離によって入力処理とトークン生成を独立してスケールできるようになった」と説明している。

その他の主要な技術的特徴として、Kubernetes Gateway API Inference Extension（GAIE）を活用したプレフィックスキャッシュ対応ルーティング、LeaderWorkerSet（LWS）プリミティブによるマルチノードレプリカとエキスパート並列処理、GPU・TPU・CPU・ストレージを横断した階層的KVキャッシュオフロードが挙げられる。

## ベンチマーク結果

マルチテナントSaaSシナリオにおいて、Qwen3-32Bモデルを16基のNVIDIA H100 GPUで実行した場合、llm-dはTime-to-First-Token（TTFT）レイテンシをほぼゼロに維持しながら約12万トークン/秒のスループットを達成し、高負荷時にベースラインのKubernetesサービスを大幅に上回るパフォーマンスを示した。

## 今後の展望

Red Hatのエンジニアリングディレクター Robert Shaw氏は、今後の優先事項としてマルチテナントモデルサービング、リクエスト優先順位付け、新しいアクセラレータへの対応、Kubernetes上のエージェントシステム向けセキュリティ強化を挙げている。また、CNCFのAI Conformanceプログラムとの連携を通じて、分離型サービング機能のエコシステム間相互運用性の確保と、推論性能測定のためのオープンなベンチマーク標準の策定も計画されている。Mistral AIもLeaderWorkerSet向けのDisaggregatedSetオペレータの開発にコミットしており、コミュニティ主導でのエンタープライズ推論基盤の標準化が進む見通しだ。
