---
date: "2026-04-11T18:12:39+09:00"
title: "AWSとGoogle Cloudがマルチクラウドネットワーク接続をプレビュー公開、専用暗号化リンクを数分で構築可能に"
description: "AWSとGoogle Cloudが共同でマルチクラウドインターコネクトサービスのプレビューを発表し、両クラウド間にMACsec暗号化された専用プライベート接続を数分で構築できる仕組みを提供する。"
tags:
  - Cloud
references:
  - "https://www.ciodive.com/news/aws-google-link-cloud-products/806705/"
  - "https://www.infoq.com/news/2025/12/aws-gcp-multicloud-networking/"
  - "https://aws.amazon.com/interconnect/multicloud/"
  - "https://cloud.google.com/blog/products/networking/aws-and-google-cloud-collaborate-on-multicloud-networking/"
  - "https://cloud.google.com/blog/products/networking/extending-cross-cloud-interconnect-to-aws-and-partners/"
---

## 概要

AWSとGoogle Cloudは共同で、マルチクラウド環境向けのプライベートネットワーク接続サービスを発表した。AWSは「AWS Interconnect - multicloud」、Google Cloudは「Cross-Cloud Interconnect」として、それぞれプレビュー提供を開始した。このサービスにより、企業はAWSマネジメントコンソール上からGoogle Cloud VPCへの専用低遅延リンクを直接プロビジョニングできるようになる。従来は数週間から数ヶ月を要していたクロスクラウド接続のセットアップが、数分で完了する点が大きな特徴だ。プレビュー期間中は、両クラウド間のマネージドプライベート接続料金は無料で提供される。

## 技術的な詳細

本サービスのバックボーンには、GitHubで公開されている「Connection Coordinator API Specification」と呼ばれるオープン標準が採用されている。これはOpenAPI 3.0に準拠した対称APIで、クラウドプロバイダー間でLayer 3のマネージド接続を調整するための仕様を定義している。接続確立に際してユーザーが手動で回線・ルーター・ルーティングプロトコルを設定する必要はなく、接続先クラウド、宛先リージョン、必要な帯域幅を指定するだけで接続が自動的にプロビジョニングされる。

セキュリティ面では、AWSとGoogle Cloudのエッジルーター間のすべてのトラフィックが**MACsec暗号化**によりデフォルトで保護される仕組みとなっており、暗号化セッションがアクティブな場合にのみデータが送受信されるようハードウェアが制御される。AWSサービスとしてはAWS Transit Gateway、AWS Cloud WAN、Amazon VPCとの統合をサポートし、物理的に分離した相互接続設備による4重冗長性を実現している。現在は米国（バージニア北部・オレゴン）および欧州（フランクフルト）を含む5リージョンで利用可能だ。両社が継続的なプロアクティブ監視を実施し、障害の検出と解決に当たる体制も整えられている。

## 背景と業界への影響

マルチクラウド戦略を採用する企業にとって、クラウド間の安定したプライベート接続の確保は長年の課題だった。これまでは専用回線の手配やルーター設定など複雑な作業を各社が個別に行う必要があり、コストと時間の両面で大きな障壁となっていた。Salesforceは本サービスについて「内部のAWSリソースをデプロイするのと同様の手軽さでクラウド間データ統合が実現できる」と評価しており、大規模エンタープライズでの実用性が期待される。

オープン標準として設計されたConnection Coordinator API仕様は、他のクラウドプロバイダーへの採用も想定しており、Microsoft Azureが2026年中に対応を予定していることが明らかにされている。主要3クラウド間でのネイティブ相互接続が標準化されれば、特定クラウドへのロックインを懸念する企業にとって、より柔軟なマルチクラウド戦略の選択肢が広がることになる。
