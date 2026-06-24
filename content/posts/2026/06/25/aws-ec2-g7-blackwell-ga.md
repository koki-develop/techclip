---
date: "2026-06-25T02:42:08+09:00"
title: "AWSがNVIDIA Blackwell GPU搭載EC2 G7インスタンスを一般提供開始、AI推論性能が前世代比4.6倍に"
description: "AWSがNVIDIA RTX PRO 4500 Blackwell Server Edition GPUを搭載したAmazon EC2 G7インスタンスの一般提供を開始し、G6比でAI推論4.6倍・グラフィックス2.1倍の性能向上を実現した。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/blogs/aws/announcing-amazon-ec2-g7-instances-accelerated-by-nvidia-rtx-pro-4500-blackwell-server-edition-gpus/"
---

## 概要

AWSは2026年6月18日、NVIDIA RTX PRO 4500 Blackwell Server Edition GPUを搭載した新世代のGPUインスタンス「Amazon EC2 G7」の一般提供（GA）開始を発表した。AWSは大手クラウドプロバイダーとして初めてこのGPUをサポートする企業となる。現在、米国東部（オハイオ）および米国西部（オレゴン）リージョンで利用可能で、AI推論やグラフィックスレンダリング、ビデオトランスコーディングなど多様なワークロードに対応している。

G7インスタンスは前世代のG6と比較して大幅な性能向上を実現している。AI推論性能は最大4.6倍、グラフィックス性能は最大2.1倍に向上したほか、GPUメモリ容量は1.33倍、GPUメモリ帯域幅は2.45倍、ネットワーク帯域幅は7倍（700 Gbps）に拡大した。さらに同時ビデオストリーム処理能力も1.5倍に向上しており、あらゆる面で前世代を上回る。

## 技術仕様とインスタンスサイズ

G7インスタンスは`g7.2xlarge`から`g7.48xlarge`まで7つのサイズを提供する。最大構成である`g7.48xlarge`および`g7.metal`では、GPU 8基（各32GB VRAM、合計256GB）、192 vCPU、768 GiBのシステムメモリ、最大7.6TBのNVMe SSDローカルストレージ、700 Gbpsのネットワーク帯域幅を備える。

対応OSはAmazon Linux、Ubuntu、RHEL、Windows Serverで、AWS Deep Learning AMI、NVIDIA Workstation AMI、またはNVIDIAドライバR595を含むカスタムEKS AMIを使用して利用できる。価格体系はオンデマンド、Savings Plans、スポットインスタンス、および12xlarge以上向けの専有インスタンスの4種類から選択可能だ。

## 対象ユースケースと今後の展開

EC2 G7インスタンスが主に想定するユースケースは、AI推論、グラフィックスレンダリング、ビデオトランスコーディング・解析、空間コンピューティング、仮想デスクトップインフラ（VDI）、そしてGPU加速データ分析など幅広い。特にBlackwellアーキテクチャの高い演算密度と大容量のGPUメモリは、大規模言語モデル（LLM）の推論や複数ストリームのリアルタイム映像処理において強みを発揮する。

現時点では米国の2リージョンのみの提供となっているが、AWSは今後さらに多くのリージョンへの展開を予定している。Blackwell世代のGPUを主要クラウドで初めて利用可能にしたことで、AWSはGPUクラウドコンピューティング市場における先行優位性を確保した形だ。
