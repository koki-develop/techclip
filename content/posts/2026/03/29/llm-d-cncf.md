---
date: "2026-03-29"
title: "Kubernetes上でLLM推論を最適化する「llm-d」がCNCF Sandboxプロジェクトに採択"
description: "Red Hat・Google・IBM・CoreWeave・NVIDIAが共同開発したKubernetesネイティブの分散LLM推論フレームワーク「llm-d」がCNCF Sandboxプロジェクトとして正式に採択された。"
tags:
  - Cloud
  - AI
references:
  - "https://www.cncf.io/blog/2026/03/24/welcome-llm-d-to-the-cncf-evolving-kubernetes-into-sota-ai-infrastructure/"
  - "https://thenewstack.io/llm-d-cncf-kubernetes-inference/"
  - "https://siliconangle.com/2026/03/24/red-hat-bets-big-kubernetes-inference-llm-d-kubeconeu/"
---

## 概要

KubeCon Europe 2026において、Red Hat・Google Cloud・IBM Research・CoreWeave・NVIDIAが共同開発したKubernetesネイティブの分散LLM推論フレームワーク「llm-d」がCNCF Sandboxプロジェクトとして正式に採択された。2025年5月に立ち上げられた同プロジェクトは、「任意のモデル、任意のアクセラレータ、任意のクラウド」での展開を可能にすることを掲げており、LLMの分散推論をクラウドネイティブの第一級ワークロードとして扱うことを目指している。AMD、Cisco、Hugging Face、Intel、Lambda、Mistral AI、カリフォルニア大学バークレー校、シカゴ大学など多くの企業・研究機関もコントリビューターとして参加しており、エンタープライズ向けLLM推論基盤の標準化に向けた大きな一歩となる。

## 技術的なアーキテクチャ

llm-dの中核的なイノベーションは、推論処理を「プリフィル（入力トークンの処理）」と「デコード（出力トークンの生成）」の2つのステージに分離する「Disaggregated Serving」アーキテクチャにある。これにより各ステージを独立してスケーリングでき、IT運用チームはレイテンシとリソース割り当てをきめ細かく制御できるようになる。

主要な技術的特徴として、Kubernetes Gateway API Inference Extension（GAIE）を活用したプレフィックスキャッシュ対応のルーティング、LeaderWorkerSet（LWS）プリミティブによるマルチノードレプリカとエキスパート並列処理、GPU・TPU・CPU・ストレージ各階層にまたがる階層的KVキャッシュオフロードなどが挙げられる。KServe（高レベル制御プレーン）とvLLM（低レベル推論エンジン）の間を橋渡しし、ベンダー中立なインフラを提供する設計となっている。

## パフォーマンスと実績

Qwen3-32Bモデルを8つのvLLMポッド・16基のNVIDIA H100 GPUで実行したベンチマークでは、負荷増大時もほぼゼロレイテンシを維持し、スループットは約120,000トークン/秒に達した。評価指標にはTime to First Token（TTFT）、Time Per Output Token（TPOT）、トークンスループット、KVキャッシュ使用率が用いられており、従来のKubernetesサービスと比較して大幅な性能改善が確認されている。

## 今後の展望

Red HatのAI CTO Brian Stevens氏は「AIの運用はいずれCIOの課題になる。そして今日のCIOが話す言語はKubernetesだ」と述べており、既存のKubernetes運用モデルにLLM推論を統合することの重要性を強調した。今後のロードマップにはマルチテナント対応のモデルサービング、リクエストの優先度制御、新しいアクセラレータへの対応、エージェントシステム向けのセキュリティ強化が含まれている。また、PyTorch Foundationとのパートナーシップによるモデル開発からクラウドネイティブサービングまでのエンドツーエンド連携や、CNCFのAI Conformanceプログラムとの相互運用性の確保も計画されている。
