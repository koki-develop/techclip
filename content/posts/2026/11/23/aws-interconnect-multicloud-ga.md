---
date: "2026-11-23T18:11:58+09:00"
title: "AWS、他社クラウドとのプライベート接続サービス「AWS Interconnect」を正式提供開始"
description: "AWSがマルチクラウド間の接続を簡素化する新サービス「AWS Interconnect」のGAを発表し、既に対応していたGoogle CloudおよびOracle Cloud Infrastructureに加え、新たにMicrosoft Azureとの接続にも対応したと発表した。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/11/aws-announces-AWS-interconnect-multicloud-azure-ga/"
---

## 概要

AWSは11月17日、複数のクラウドプロバイダー間の接続を簡素化する新サービス「AWS Interconnect」の一般提供(GA)を開始したと発表した。AWSはこれを「その種のものとして初めて目的専用に構築されたプロダクト」と位置づけており、マルチクラウド構成を採用する企業向けに、従来は自前で構築する必要があったクラウド間の接続基盤を、マネージドなプライベート接続として迅速にプロビジョニングできるようにする。AWS Interconnectは既にGoogle CloudおよびOracle Cloud Infrastructure(OCI)に対応しており、今回のGAで新たにMicrosoft Azureにも対応した。

## Azureとの接続とオープン仕様

AWS Interconnectの要となるのは、クラウド間を直接つなぐプライベート接続をオープンな仕様に基づいて実現している点だ。Microsoftは2026年8月にAzure側での対応をパブリックプレビューとして発表しており、このオープン仕様を採用した最新のクラウドサービスプロバイダー(CSP)となった。今回のGAにより、AWSとAzureの顧客は従来必要だった複雑な自社構築型のマルチクラウド接続アプローチを経ずに、両社のクラウド環境をプライベートかつスケーラブルに結べるようになる。AWSは、Google Cloud・OCIが既に同じ仕様に対応していることで、顧客がどのクラウド組み合わせを選んでも統一された接続体験を得られるとしている。

## 対応リージョンと利用方法

現時点でAWS Interconnectが利用可能なのは、米国東部(バージニア州)、アジア太平洋(シドニー)、ヨーロッパ中部(フランクフルト)の3リージョンである。利用者はAWS Management Console、CLI、APIのいずれからでも接続の作成・管理が行える。具体的な料金体系は今回の発表では明示されていない。

## 今後の展望

マルチクラウド運用は多くの企業にとって既に既定路線となっているが、クラウド間の専用線接続はこれまで各社が個別に調整・構築するコストの高い作業だった。AWS Interconnectがオープン仕様のもとでAzureとの接続を皮切りに展開されることで、クラウド間接続が標準化されたサービスとして扱われる流れが強まる可能性がある。Google CloudおよびOCIは既にこの仕様に対応済みであり、今後は、対応リージョンの拡大とともに、マルチクラウドネットワーキングの選択肢として注目される見込みだ。
