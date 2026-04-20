---
date: "2026-04-21T02:29:40+09:00"
title: "Amazon EC2 C8in/C8ibインスタンスがGA、第6世代Intel Xeon搭載で最大600Gbpsのネットワーク帯域幅を実現"
description: "AWSがAWS専用カスタム第6世代Intel Xeon Scalableプロセッサを搭載したコンピューティング最適化インスタンス「C8in」「C8ib」の一般提供を開始し、前世代比最大43%の性能向上を達成した。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/04/amazon-ec2-c8in-c8ib-instances-ga/"
  - "https://aws.amazon.com/blogs/aws/aws-weekly-roundup-claude-opus-4-7-in-amazon-bedrock-aws-interconnect-ga-and-more-april-20-2026/"
---

## 概要

AWSは2026年4月16日、Amazon EC2の新世代コンピューティング最適化インスタンス「C8in」および「C8ib」の一般提供（GA）を開始した。両インスタンスはAWS専用にカスタマイズされた第6世代Intel Xeon Scalableプロセッサと最新の第6世代AWS Nitroカードを搭載しており、前世代のC6inと比較して最大43%の性能向上を実現している。最大384 vCPUまで拡張可能で、大規模かつ高負荷なワークロードに対応する。

## インスタンスの特徴と用途

C8inとC8ibはそれぞれ異なるI/Oのボトルネックに特化して設計されている。C8inはネットワーク集約的なワークロード向けに最適化されており、最大600Gbpsのネットワーク帯域幅を提供する。分散コンピューティング、大規模データ分析といった用途に適している。一方、C8ibは高性能な商用データベースやファイルシステム向けで、最大300GbpsのEBS帯域幅を持ち、I/O集約型のストレージワークロードに対応する。

## 利用可能なリージョンと購入オプション

C8inは米国東部（バージニア北部）、米国西部（オレゴン）、アジア太平洋（東京）、ヨーロッパ（スペイン）の4リージョンで利用可能だ。C8ibは現時点で米国東部（バージニア北部）と米国西部（オレゴン）の2リージョンに対応している。いずれもオンデマンド、Savings Plans、スポットインスタンスの3つの購入オプションで利用できる。東京リージョンでC8inが利用可能になったことは、日本国内でネットワーク性能を必要とするユーザーにとって特に注目すべき点だ。
