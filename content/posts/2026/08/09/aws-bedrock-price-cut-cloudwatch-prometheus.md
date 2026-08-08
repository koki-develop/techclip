---
date: "2026-08-09T08:05:42+09:00"
title: "AWS、Bedrock上のGPT-5.6を最大80%値下げ、CloudWatchにPrometheusメトリクス無エージェント収集機能"
description: "AWSがBedrock上のOpenAI GPT-5.6モデルを最大80%値下げし、CloudWatchにはエージェント不要でPrometheusメトリクスを収集できるフルマネージド型コレクターが追加された。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/blogs/aws/aws-weekly-roundup-price-reduction-of-gpt-models-in-bedrock-cloudwatch-managed-collectors-for-prometheus-metrics-and-more-august-3-2026/"
---

## 概要

AWSは2026年8月3日公開の週次まとめ記事「AWS Weekly Roundup」で、Amazon Bedrock上のOpenAI GPT-5.6モデルの大幅値下げと、Amazon CloudWatchへのPrometheusメトリクス向けフルマネージド型コレクター追加を発表した。両施策とも、AIワークロードおよび監視運用にかかるコストと運用負担の軽減を狙ったものである。

## Bedrock上のGPTモデル値下げ

Bedrock上で提供されるGPT-5.6には「Luna」と「Terra」の2つのバリエーションがあり、2026年7月30日付でオンデマンド推論価格がそれぞれ引き下げられた。GPT-5.6 Lunaは価格が80%引き下げられ、入力トークン100万あたり0.20ドル、出力トークン100万あたり1.20ドルという水準になった。一方、GPT-5.6 Terraの価格は20%引き下げとなっている。値下げは既存ユーザーにも自動的に適用される形で実施されており、追加の設定変更は不要である。

## CloudWatchのPrometheusメトリクス管理型コレクター

Amazon CloudWatchには、AWSインフラストラクチャからPrometheus形式のメトリクスを収集するフルマネージド型コレクターが新たに追加された。この機能により、Amazon EKS、Amazon EC2、Amazon ECS、Amazon MSK、Amazon OpenSearch Serviceといった主要ワークロードのメトリクスを、エージェントのデプロイや管理を一切行うことなく収集できるようになる。従来、Prometheus形式のメトリクス収集にはユーザー自身がスクレイピング用のインフラを構築・維持する必要があったが、この負担が解消される。

## その他のアップデート

同じ週次まとめでは、OCI(Oracle Cloud Infrastructure)向けのマルチクラウド接続を可能にするAWS Interconnectの一般提供(GA)開始、IAM Identity Centerにおけるディレクトリのマルチリージョン対応拡張、Amazon S3 TablesでのApache Iceberg V3 Variantデータ型サポート追加なども紹介されている。

## 今後の展望

GPTモデルの大幅値下げは、Bedrock上でOpenAIモデルを利用する開発者にとって導入・運用コストの引き下げに直結する。また、CloudWatchのPrometheus管理型コレクターは、Kubernetesやコンテナ環境を中心に監視の運用自動化を進める企業にとって、既存のPrometheusベースの可観測性スタックをAWSネイティブな形でよりシンプルに統合する選択肢となりそうだ。
