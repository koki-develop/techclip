---
date: "2026-04-17T02:37:23+09:00"
title: "NVIDIAが量子コンピュータ向けオープンAIモデル「Ising」を発表——キャリブレーションとエラー訂正を大幅強化"
description: "NVIDIAは量子コンピュータの実用化を加速するオープンAIモデルファミリー「Ising」を発表し、エラー訂正デコーディングで従来比最大2.5倍高速・3倍高精度を実現した。"
tags:
  - AI
references:
  - "https://nvidianews.nvidia.com/news/nvidia-launches-ising-the-worlds-first-open-ai-models-to-accelerate-the-path-to-useful-quantum-computers"
  - "https://developer.nvidia.com/blog/nvidia-ising-introduces-ai-powered-workflows-to-build-fault-tolerant-quantum-systems/"
  - "https://www.tomshardware.com/tech-industry/artificial-intelligence/nvidia-releases-ising-open-ai-models"
---

## 概要

NVIDIAは2026年4月14日、量子コンピューティング向けとしては世界初のオープンAIモデルファミリー「NVIDIA Ising」を発表した。量子コンピュータの実用化における主要な障壁である「キャリブレーション」と「量子エラー訂正（QEC）」の2領域をAIで解決することを目指したモデル群で、研究機関や企業が自社のハードウェアに合わせてカスタマイズできるオープンアーキテクチャで提供される。CEOのジェンセン・ファン氏は「AIは量子コンピューティングを実用化するために不可欠であり、AIが量子マシンの制御プレーンになる」と述べ、AIと量子の融合を同社の重要戦略と位置づけた。

## 2つのモデルの技術仕様

Isingファミリーは用途の異なる2種類のモデルで構成される。**Ising Calibration**は350億パラメータのビジョン言語モデル（VLM）で、超伝導量子ビット・量子ドット・イオントラップなど複数の量子ビット方式から生成されたデータで学習されている。量子プロセッサのキャリブレーション作業を自動化し、従来は数日を要していた調整時間を数時間に短縮することが可能だ。**Ising Decoding**は量子エラー訂正デコーディング専用の3D畳み込みニューラルネットワーク（CNN）で、処理速度を優先した91万2,000パラメータの「Fast版」と、精度を優先した179万パラメータの「Accurate版」の2バリアントが用意されている。

## 性能ベンチマークと導入状況

Ising Decodingの性能評価では、量子エラー訂正の標準的なオープンソースデコーダ「PyMatching」と比較して最大2.5倍の高速化と3倍の精度向上を達成した。具体的にはd=13・p=0.003の条件でPyMatchingより2.25倍高速、論理エラー率で1.53倍の改善が確認されている。Ising Calibrationは独自の量子キャリブレーション評価指標「QCalEval」において既存の大規模言語モデルを上回る結果を示した。すでにAcademia Sinica、フェルミ国立加速器研究所、ハーバード大学、Infleqtion、IQM Quantum Computersといった学術機関や量子スタートアップが採用を表明している。

## 展開環境と今後の展望

モデルのデプロイには、TensorRT、CUDA-Q QEC、PyTorchベースのトレーニングフレームワークを組み合わせたレシピが提供される。NVIDIAのCUDA-Qプラットフォームおよび量子GPU相互接続技術「NVQLink」との統合も予定されており、量子GPUスーパーコンピュータへのスケーリングを見据えたロードマップが示されている。オープンアーキテクチャを採用しているため、各組織は固有のハードウェア特性に合わせてモデルをファインチューニングでき、独自データをオンサイトで管理できる点も研究機関にとってのメリットとなっている。量子コンピューティング市場は2030年に110億ドルを超えると予測されており、NVIDIAはAIとの融合によって同市場の主要プレイヤーとしての地位を確立しようとしている。
