---
date: "2026-04-14T02:30:55+09:00"
title: "Google CloudがNVIDIA GTC 2026で分数G4 VMとVera Rubin NVL72対応を発表"
description: "Google CloudはNVIDIA GTC 2026に合わせ、分数GPU割り当て対応のG4 VMプレビューと、2026年後半にNVIDIA Vera Rubin NVL72ラックスケールシステムを提供する計画を発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/compute/google-cloud-ai-infrastructure-at-nvidia-gtc-2026"
  - "https://www.digitalapplied.com/blog/google-cloud-gtc-2026-vera-rubin-nvl72-rack-systems"
  - "https://virtualizationreview.com/articles/2026/03/20/nvidia-aws-and-google-cloud-spotlight-ai-infrastructure-push-at-gtc-2026.aspx"
---

## 概要

Google CloudはNVIDIA GTC 2026に合わせ、AIインフラに関する複数の強化策を発表した。主な内容は、NVIDIA RTX Pro 6000 Blackwell Server Edition GPUを搭載したG4 VMの分数スライス提供のプレビューと、2026年後半にNVIDIA Vera Rubin NVL72ラックスケールシステムを提供する初期クラウドの一つとなる計画だ。これらの取り組みはGoogle CloudのAI Hypercomputerアーキテクチャの一環として位置づけられており、TPUと並ぶNVIDIAネイティブな選択肢を顧客に提供することを目的としている。

## 分数G4 VMによる柔軟なGPUリソース割り当て

今回プレビューが発表された分数G4 VMは、NVIDIA vGPU技術を活用し、1つのGPUを1/2・1/4・1/8のスライスに分割して提供する。これはNVIDIA RTX Pro 6000 Blackwell Server Edition向けとしては業界初の取り組みとされ、推論・レンダリング・リモートデスクトップ・ストリーミングなど、フルGPUを必要としない多様なワークロードに対してリソースを適切なサイズで割り当てられる点が特徴だ。Dynamic Workload Schedulerと組み合わせることで、フォールバック優先度の設定や利用可能なGPU構成の自動検索も可能となり、GPUの取得しやすさが大幅に向上する。G4 VMは30Bから100B以上のパラメータを持つモデルのファインチューニングや推論にも適した性能を持つ。

## NVIDIA Vera Rubin NVL72による大規模AIトレーニング

2026年後半に提供が予定されているNVIDIA Vera Rubin NVL72は、1ラックに72基のGPUをNVLink 6インターコネクトで接続したラックスケールシステムだ。FP8トレーニング性能は1.4 exaFLOPsに達し、これは従来のH100構成（1ラックあたり約720 petaFLOPS）と比べて約2倍に相当する。NVLink 6によるテンソル並列処理はGPU間のデータ転送オーバーヘッドを排除し、オンプレミスのNVIDIA DGX SuperPOD環境に匹敵する大規模LLMトレーニングをクラウドで実現可能にする。

Google CloudはこのVera Rubin NVL72向けに新しいA4 Ultraインスタンスファミリーを用意しており、2026年第2四半期からus-central1とeurope-west4でプレビューアクセスが開始される予定だ。フルラック（72 GPU）とサブラック構成の両方が提供され、企業や研究機関はGoogle Cloudコンソールからプレビュー申し込みができる。

## ソフトウェア統合と競争戦略

ハードウェア面の強化に加え、Google CloudはNVIDIA DynamoをGoogle Kubernetes Engine Inference Gatewayと統合することも発表した。これにより、アプリケーション層とハードウェア層にまたがるモジュラーかつオープンソースのコントロールプレーンが実現する。

競合他社のAWSやAzureが高密度NVIDIAコンピュートで先行してきた中、今回の発表はGoogle Cloudが大規模トレーニングワークロードの獲得に本腰を入れることを示している。また、既存のTPU v5インフラとの共存戦略として「TPUネイティブとNVIDIAネイティブの両方を同一エコシステム内で選択できる環境」の構築が明確に打ち出された形だ。
