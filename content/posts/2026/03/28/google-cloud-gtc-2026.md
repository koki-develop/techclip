---
date: "2026-03-28"
title: "Google Cloud、NVIDIA GTC 2026で分数GPU VMやVera Rubin NVL72対応など次世代AIインフラを発表"
description: "Google CloudがNVIDIA GTC 2026で、GPUを1/2〜1/8単位で利用できる分数G4 VMのプレビュー、Vera Rubin NVL72ラックスケールシステムの対応計画、NVIDIA DynamoとGKEの統合を発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/compute/google-cloud-ai-infrastructure-at-nvidia-gtc-2026"
---

## 概要

Google Cloudは2026年3月28日、NVIDIA GTC 2026において、AIクラウドインフラストラクチャの大幅な強化を発表した。今回の発表は、GPUリソースの柔軟な利用を可能にする分数GPU VM、次世代ラックスケールシステムVera Rubin NVL72への対応、そしてNVIDIA DynamoとGoogle Kubernetes Engine（GKE）の統合という3つの柱で構成されている。単なるGPUの提供にとどまらず、AIインフラをクラウドスタック全体の課題として捉え、柔軟な消費モデルと深いソフトウェア統合を重視する姿勢が示された。

## 分数G4 VM：GPUの柔軟な分割利用

Google Cloudは、NVIDIA RTX PRO 6000 Blackwell Server Edition GPUを搭載した分数G4 VMのプレビューを発表した。NVIDIAの仮想GPU（vGPU）技術を活用し、GPUを1/2、1/4、1/8単位で分割して利用できる新しい構成を提供する。これにより、推論、レンダリング、リモートデスクトップ、ストリーミングなどのワークロードに対して、必要なリソースを過不足なく割り当てることが可能になる。

さらに、Dynamic Workload Schedulerと組み合わせることで、分数スライスのフォールバック優先度を設定でき、スケジューラが自動的に利用可能なGPU構成を見つけることで、リソースの取得可能性が大幅に向上する。AI推論のコスト効率化を求める企業にとって、フルGPUを占有せずに済む選択肢が広がる形だ。

## Vera Rubin NVL72ラックスケールシステムへの対応

Google Cloudは、2026年後半にNVIDIA Vera Rubin NVL72ラックスケールシステムを提供する最初のクラウドプロバイダーの一つとなる計画を明らかにした。このシステムはAI Hypercomputerアーキテクチャに統合され、新たにA4 Ultraインスタンスファミリーとして提供される。

A4 Ultraは、1ラックあたり72基のVera Rubin GPUをNVLink 6で接続し、FP8精度で1.4エクサFLOPSの演算性能を実現する。NVLink 6はH100システムで使用されるNVLink 4と比較してリンクあたりの帯域幅が2倍となり、学習時の勾配同期の高速化やModel FLOP Utilization（MFU）の改善が期待される。プレビューは2026年第2四半期にus-central1およびeurope-west4リージョンで開始され、一般提供は2026年後半、さらなるリージョン拡大は2027年を見込む。

なお、Google CloudはNVL72をTPU v5e/v5pインフラと並行して提供する方針であり、CUDA対応のトレーニングワークロードにはNVL72を、JAX最適化された推論にはTPUをという形で、マルチアクセラレータ戦略を維持する。

## NVIDIA DynamoとGKE Inference Gatewayの統合

ソフトウェア面では、NVIDIA DynamoとGKE Inference Gatewayの統合が発表された。これにより、アプリケーション層からハードウェアまでをカバーするモジュラーかつオープンソースのコントロールプレーンが提供される。Kubernetesベースの推論デプロイメントにおいて、GPUリソースの管理と推論ワークロードのオーケストレーションがより効率的に行えるようになる。

Google Cloudの今回の発表は、AWS、Microsoft Azure、OCIといった他の主要クラウドプロバイダーもVera Rubinベースのインスタンスを2026年中に展開する中で、柔軟性とソフトウェア統合の深さで差別化を図る戦略を鮮明にしたものと言える。
