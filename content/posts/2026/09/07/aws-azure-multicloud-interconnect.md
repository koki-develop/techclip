---
date: "2026-09-07T18:18:21+09:00"
title: "AWSとAzureが直結サービスを相次ぎプレビュー公開、主要3クラウド全てとのプライベート接続が数クリックで完結へ"
description: "AWSとMicrosoft Azureが「AWS Interconnect」と「Azure Multicloud Interconnect」を通じて協業し、オープンAPIとMACsec暗号化・クワッド冗長構成による高可用なクラウド間直結をパブリックプレビューで開始した。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/blogs/networking-and-content-delivery/aws-and-microsoft-azure-collaborate-to-expand-multicloud-networking/"
  - "https://azure.microsoft.com/en-us/blog/introducing-azure-multicloud-interconnect-for-aws/"
  - "https://www.itpro.com/cloud/cloud-computing/multi-cloud-with-aws-and-azure-just-got-a-whole-lot-easier-thanks-to-a-new-interconnect-service"
---

## 概要

AWSとMicrosoft Azureは8月31日、両クラウド間のプライベート接続を大幅に簡素化する協業を発表した。AWS側は現在パブリックプレビュー中の「AWS Interconnect」を、Azure側は新サービス「Azure Multicloud Interconnect」を通じて連携し、オープンなAPI仕様に基づいたオンデマンドの直接接続を提供する。これにより、AWSはGoogle Cloud、Oracle Cloud Infrastructure（OCI）に続いてAzureとも直結を実現し、主要3大クラウド全てとプライベートネットワークで結ばれることになった。ITProの報道によれば、AWSとGoogle Cloudも2025年12月に同様の協業を発表しており、今回の提携はその流れを引き継ぐ形だ。

## 技術的な特徴

新サービスの中核は、両社が共同でGitHub上に公開したオープンAPI仕様にある。このAPIを軸に、AWSの「AWS Interconnect」とAzureの「Azure Multicloud Interconnect」が相互に連携し、追加のクラウドプロバイダーも将来的に同じ枠組みに参加できる設計になっている。セキュリティ面ではMACsec暗号化をデフォルトで実装し、エッジルータ間の通信を保護する。可用性については、物理的に異なる複数の相互接続施設とルータを経由する4つの独立した論理パス、いわゆる「クワッド冗長化」構成を採用し、サイト全体の障害が発生しても業務を継続できるようにした。Azure側はこの構成で99.99%の可用性を掲げ、初期速度100Gbpsからの動的スケーリングにも対応する。Azure Private Linkとの統合により、エンドツーエンドのプライベート接続も可能だ。プレビューは米国東部（バージニア北部)・米国西部（カリフォルニア北部）・アジア太平洋（シドニー）・欧州（フランクフルト）のリージョンで利用できる。

## 従来の課題と業界背景

これまで、AzureとAWSの環境をプライベートに接続するには、物理的な相互接続の手配や複数コンポーネントの手作業での組み立てなど、数週間から数ヶ月に及ぶ慎重な計画が必要だった。AWSのネットワーキング担当VPであるRobert Kennedy氏は、顧客から「既存の接続方法が煩雑だ」との指摘が寄せられてきたと述べ、新サービスでは数クリック・数分でプロビジョニングが完了すると説明する。AzureのネットワーキングサービスVPも「Azure Multicloud Interconnectはこのモデルを根本的に変える」とコメントしている。背景には、企業のマルチクラウド戦略が急速に一般化している実情がある。ITProが引用したEquinixの調査では、企業の42%がハイブリッド/マルチクラウド環境で全ワークロードの25〜50%を実行しており、85%が10〜50のクラウドに接続しているという。M&Aや業界特有の規制要件によって複数クラウドの併用を迫られるケースも増えており、こうした需要が今回の協業を後押ししたとみられる。

## 今後の展望

両社は今後、対応リージョンの拡大や帯域幅オプションの追加、顧客フィードバックに基づく機能改善を計画しているとしている。オープンAPI仕様を軸に据えたことで、ハイパースケーラーやネットワークサービスプロバイダー、通信事業者が共通の相互運用フレームワークを採用し、クラウド間のシームレスな接続が業界標準になっていく可能性も示唆されている。運用の複雑さとコストがマルチクラウド採用の障壁となってきた中、主要3大クラウドすべてが直結可能になったことで、企業のクラウド戦略における自由度は一段と高まりそうだ。
