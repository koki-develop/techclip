---
date: "2026-05-16T02:36:23+09:00"
title: "AWSがIntel Xeon 6搭載の新世代EC2インスタンス群とElastiCache Valkey 9.0を発表"
description: "AWSはカスタムIntel Xeon 6搭載のR8idn/R8idb/M8idn/M8idbインスタンスと、フルテキスト検索や最大40%スループット向上を含むElastiCache Valkey 9.0の一般提供開始を発表した。"
tags:
  - Cloud
references:
  - "https://finopsweekly.com/news/aws-updates-2026-05-14/"
  - "https://aws.amazon.com/about-aws/whats-new/2026/05/aws-lambda-managed-instances/"
  - "https://aws.amazon.com/about-aws/whats-new/2026/05/valkey-amazon-elasticache/"
  - "https://aws.amazon.com/blogs/database/announcing-valkey-9-0-for-amazon-elasticache/"
  - "https://aws.amazon.com/ec2/instance-types/r8i/"
---

## 概要

AWSは2026年5月、カスタムIntel Xeon 6プロセッサを搭載した新世代EC2インスタンスファミリー（R8idn/R8idb/M8idn/M8idb）の提供開始と、Amazon ElastiCacheにおけるValkey 9.0の一般提供（GA）を相次いで発表した。あわせてAWS Lambda Managed InstancesがAmazon EventBridge Schedulerによるスケジュールスケーリングに対応し、コスト最適化の選択肢が広がった。いずれもAIワークロードやリアルタイム分析を念頭に置いた機能強化となっている。

## Intel Xeon 6搭載の新世代EC2インスタンス

新インスタンスファミリーはすべてカスタムIntel Xeon 6プロセッサを採用しており、前世代（R6idn/M6idn）比で最大43%高いvCPUあたり性能と、3.3倍のメモリ帯域幅を実現する。

- **R8idn**: 最大600Gbpsのネットワーク帯域（拡張ネットワーキング対応EC2最高値）と最大22.8TBのNVMe SSDローカルストレージを備え、インメモリデータベース・リアルタイムビッグデータ分析・AI/ML推論キャッシュなど、ネットワーク集約型のメモリ集中ワークロード向け。最大構成（96xlarge）は384vCPU/3,072GiBメモリ。
- **R8idb**: EBS帯域幅を最大300Gbps、IOPSを最大144万まで引き上げ、非アクセラレーテッド型EC2で最高のEBS性能を誇る。大規模商用データベースやデータレイク向けに設計されている。
- **M8idn**: 汎用バランス型ながら同様に600Gbpsネットワーク帯域と22.8TBのNVMeストレージを提供。マイクロサービスやアプリケーションサーバーで高いI/Oが求められる場面に適する。

ネットワーク帯域幅とEBS帯域幅の間で最大25%を柔軟に振り分けられる「フレキシブルバンドウィス」機能も引き続き搭載している。

## ElastiCache Valkey 9.0の主要新機能

2026年5月5日にGAとなったValkey 9.0は、追加料金なしで全商用AWSリージョン・GovCloud・中国リージョンのノードベースクラスターおよびサーバーレスキャッシュで利用できる。主な新機能は以下の4点だ。

1. **フルテキスト・ハイブリッド検索**: 既存のベクトル類似検索を拡張し、テキスト関連度とベクトル類似度を組み合わせたハイブリッド検索を提供。数テラバイトのデータに対してマイクロ秒レベルの低遅延でフルテキスト検索・セマンティック検索・フィルタリング・集計が可能になり、Amazon BedrockやOpenAIのエンベディングをリアルタイムで処理できる。
2. **パイプライン処理のスループット向上**: コマンド解析の高速化とメモリプリフェッチ最適化により、パイプライン型ワークロードで最大40%のスループット向上を実現。
3. **ハッシュフィールドの有効期限（TTL）**: ハッシュ内の個別フィールドに対してTTLを設定可能になり、ユーザープロフィール中の認証コードのみを期限切れにするといった細粒度なデータライフサイクル管理が可能になった。
4. **クラスターモードでのマルチデータベースサポート**: マルチテナント環境でキープレフィックスの管理が不要な軽量な名前空間として機能し、アプリケーションの複雑性を低減する。このほかジオスパティアルクエリへのポリゴン検索サポートも追加された。

## Lambda Managed Instancesのスケジュールスケーリング

同期的に発表されたAWS Lambda Managed Instancesのスケジュールスケーリング対応（2026年5月12日）も注目される。EventBridge Schedulerを使い、ビジネスピーク時間前にインスタンスをスケールアップ、アイドル時間帯にゼロまでスケールダウンするスケジュールを定義できるようになった。設定はEventBridgeコンソール・AWS CLI・SDK・CDK・CloudFormationから可能で、Lambda Managed Instancesをサポートする全リージョンで利用できる。

これら一連の発表は、AWSがメモリ集約型・ネットワーク集約型のAI/リアルタイムワークロードに対応するインフラ整備を加速させていることを示している。特にValkey 9.0の検索機能強化は、ElastiCacheをキャッシュ層にとどまらずAI検索バックエンドとして活用する道を開くものであり、今後の採用事例の拡大が注目される。
