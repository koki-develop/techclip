---
date: "2026-08-11T08:09:52+09:00"
title: "Amazon ECS、EC2 G6fで分数GPUスケジューリングに対応しGPU共有によるコスト最適化を実現"
description: "Amazon ECSがEC2 G6fインスタンス上でGPUを最小1/8単位に分割して複数タスクへ割り当てる分数GPUスケジューリングに対応した。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/08/amazon-ecs-fractional-gpu/"
  - "https://mwpro.co.uk/blog/2026/08/07/amazon-ecs-now-supports-fractional-gpu-scheduling-with-amazon-ec2-g6f-instances/"
---

## 概要

Amazon ECS(Elastic Container Service)は、NVIDIA L4 Tensor Core GPUを搭載したEC2 G6fインスタンスにおいて、分数GPU(Fractional GPU)スケジューリングに対応した。従来はGPUワークロードを実行する際にインスタンス上のGPUをタスク単位で丸ごと占有する必要があったが、この機能により1基のGPUを複数のタスクで分割・共有できるようになる。小規模な推論やモデル実験など、フルGPUを必要としないワークロードにおいて、インフラコストの削減とGPU利用率の向上を両立できる点が最大のポイントだ。

## 技術的な詳細

分数GPUの割り当ては、ECSタスク定義のコンテナ定義において`GPU`パラメータに小数値を指定することで行う。対応する分割単位は1/8GPU(GPUメモリ3GB相当)、1/4GPU、1/2GPUの3種類で、それぞれ`GPU=0.125`、`GPU=0.25`、`GPU=0.5`と記述する。これにより、最小構成では1基のGPUを最大8つのタスクに分割して割り当てることが可能になる。

対応インスタンスは現時点ではEC2 G6fインスタンスのみで、ECS on EC2およびECS Managed Instancesの両方の実行モデルで利用できる。G6fインスタンスが提供されているAWSリージョンであれば、いずれの地域でも本機能を使用可能だ。設定はAWS Management Console、AWS CLI、CloudFormationなどのIaCツールから行える。ECS Managed Instancesを利用する場合は、Amazon CloudWatch Container InsightsによるGPUメトリクスの監視や、GPUハードウェア故障の自動検知・置換といった運用機能も併せて利用できる。

## 想定されるユースケース

想定される主なユースケースは、小規模な推論モデルの提供、モデル実験、グラフィックスレンダリングなど、GPUリソースを部分的にしか必要としないワークロードである。従来はこうした軽量ワークロードのためにもフルGPUインスタンスをプロビジョニングする必要があり、GPUリソースの無駄が生じやすかった。分数GPUスケジューリングにより、複数の小規模ワークロードを1基のGPU上に集約できるため、インフラコストの削減とGPUの利用効率向上が期待できる。
