---
date: "2026-03-29"
title: "AWS Load Balancer ControllerがGateway APIをGA対応、アノテーション依存からの脱却でKubernetesネットワーク管理が進化"
description: "AWSがKubernetes Load Balancer ControllerでGateway APIのGA（一般提供）サポートをリリースし、型安全なCRDベースの設定でALB・NLBの管理が可能になった。"
tags:
  - Cloud
references:
  - "https://www.infoq.com/news/2026/03/aws-gateway-api-ga/"
  - "https://aws.amazon.com/blogs/networking-and-content-delivery/aws-load-balancer-controller-adds-general-availability-support-for-kubernetes-gateway-api/"
---

## 概要

AWSは、Kubernetes Load Balancer ControllerにおけるGateway APIサポートのGA（一般提供）を発表した。これにより、Application Load Balancer（ALB）とNetwork Load Balancer（NLB）をGateway API仕様で管理できるようになり、従来のアノテーションベースの設定から型安全なCustom Resource Definitions（CRD）ベースの設定へと移行が可能になった。Gateway APIはKubernetes Ingress APIの後継として位置づけられており、今回のGA対応はAWSにおけるKubernetesネットワーキングの標準化にとって重要なマイルストーンとなる。

## 技術的な詳細

今回のリリースでは、レイヤー4ルーティング（TCP、UDP、TLS、NLB経由）とレイヤー7ルーティング（HTTP、gRPC、ALB経由）の両方がサポートされる。新たに導入されたCRDとして、TargetGroupConfiguration、LoadBalancerConfiguration、ListenerRuleConfigurationの3つがあり、スキーマバリデーション付きの型安全な設定が可能になった。従来のアノテーション方式ではJSONを埋め込む形で設定していたため、スキーマバリデーションやIDEサポートがなく、実行時にエラーが発覚するリスクがあった。新しいアプローチでは、適用時に設定が検証されるため、こうした問題が解消される。

## RBACとの整合性とクロスネームスペースルーティング

Gateway APIはリソースをGatewayClass（インフラストラクチャテンプレート）、Gateway（リスナー、TLS、サブネット配置）、Routes（パスベースルーティング）の3つに分離しており、Kubernetesのロールベースアクセス制御（RBAC）の境界と自然に対応する設計となっている。これにより、プラットフォームチームが共有Gatewayをプロビジョニングし、各アプリケーションチームは自身のネームスペースからHTTPRouteを作成して参照するという運用が、クラスタ管理者権限なしで実現できる。GitOpsフレンドリーなYAML設定との親和性も高く、開発者体験の向上にも寄与する。

## 今後の展望

なお、AWSのVPC Latticeはすでにサービスメッシュのeast-west（サービス間）トラフィックにおいてGateway APIをサポートしており、今回のリリースでnorth-south（イングレス）トラフィックのカバレッジが完成した形となる。これにより、AWS上のKubernetesネットワーキングはGateway APIを共通インターフェースとして統一的に管理できる基盤が整ったと言える。
