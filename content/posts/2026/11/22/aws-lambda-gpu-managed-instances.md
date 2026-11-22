---
date: "2026-11-22T18:08:34+09:00"
title: "AWS Lambda、GPU対応Managed Instancesで最大48並列推論をサーバーレスに実現"
description: "AWS LambdaのManaged InstancesがEC2 GシリーズGPUに対応し、1GPU上でモデルを共有しながら最大48件の同時推論をサーバーレスで実行できるようになった。"
tags:
  - Cloud
  - AI
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/11/aws-lambda-gpu-managed-instances/"
  - "https://dev.classmethod.jp/en/articles/lambda-managed-instances-gpu-acceleratorconfig/"
  - "https://www.infoq.com/news/2026/11/aws-lambda-gpu-managed-instances/"
---

## 概要

AWSは11月16日から18日にかけて、AWS LambdaのManaged InstancesをEC2 Gシリーズ（NVIDIA GPU搭載インスタンス）に対応させる機能を展開した。これによりLambdaのEvent FunctionsからGPUを直接利用できるようになり、GPUドライバやCUDAバージョン、AMI、クラスタや device plugin の管理を一切行わずに、AI推論・メディア処理・3Dレンダリング・科学計算・金融シミュレーションといったGPUワークロードをサーバーレスで実行できる。対応インスタンスはg4dn（NVIDIA T4）、g5（A10G）、g6・gr6（L4）、g6e（L40S）、およびフラクショナルGPUのg6f・gr6fで、P系列やG7/G7e、Graviton版のg5gには対応していない。利用にはコンテナイメージ（Zipパッケージは不可）、x86_64アーキテクチャ、Lambda Managed Instancesの`CapacityProviderConfig`が必須となる。

## モデル共有による高い同時実行性

今回の機能の核心は、1つのGPU上で最大48件の同時実行がモデルをメモリ上で共有できる点にある。従来のサーバーレスGPU推論は実行環境ごとにモデルをロードし直すオーバーヘッドが課題だったが、Lambdaは実行環境内でモデルを共有しつつGPU利用率・CPU利用率・同時実行数に基づいて自動スケーリングする仕組みを備えた。AWSはCUDA、CuPy、PyTorchに加え、vLLMとSGLangの推論サーバー向けベースイメージを計5種類提供しており、vLLMやSGLangを使う場合は`MODEL_ID`環境変数を指定するだけでハンドラコードを書かずに推論サーバーを起動できる。モデルはHugging FaceリポジトリやModelScope、S3プレフィックス、ローカルパスのいずれからも参照可能だ。実際にGemma 4 E2Bモデルをg6.2xlarge上でvLLM経由で検証したケースでは、単一リクエストで約130トークン/秒、48件同時実行では集計スループットが3,400〜3,600トークン/秒に達し、417件のテスト呼び出しはすべて成功したという。

## 設定の詳細とパフォーマンス検証

GPUインスタンスの利用は新設の`AcceleratorConfig`で制御し、`AcceleratorMemorySize`に3・6・12・16・24・48 GiBのいずれかを指定することで実行環境あたりのGPUメモリ割り当てを決める（指定値は最小値であり実際の割り当てはそれ以上になる場合がある）。この設定を使う関数は`/tmp`の上限が32,768 MBに制限される点に注意が必要だ。スケーリング面では、キャパシティプロバイダーが新たに`LambdaCapacityProviderAverageGPUUtilization`メトリクスをサポートし、CPUベースのスケーリングと並んでGPU利用率に基づくターゲットトラッキングが可能になった。CloudWatchにも`GPUUtilization`や`GPUAllocated`、`ExecutionEnvironmentGPUUtilization`などの新メトリクスが追加されている。dev.classmethodの検証では、g6.xlarge（NVIDIA L4）上でPyTorch（CUDA 12.6ビルド）が追加設定なしに動作し、4096×4096行列の乗算ベンチマークでCPUの0.680秒（0.20 TFLOPS）に対しGPUは0.0103秒（13.3 TFLOPS）と約66倍の高速化を確認したという。一方で東京リージョンの一部アベイラビリティゾーンではg5/g6ファミリーが利用できず、サブネット選定の調整が必要だったことや、GPUインスタンスが「Running On-Demand G and VT instances」という別クオータを消費する点（g6.xlargeは4vCPUだがデフォルト3インスタンス構成には12vCPUのクオータが必要）も報告されている。

## 料金モデルと制約、今後の展望

料金はEC2オンデマンド料金をベースに、Lambdaの管理フィーとして9.75%（CPU実行の15%より低い）、さらにリクエスト課金として100万件あたり0.20ドルが加算される。Savings PlansやReserved Instancesも適用可能で、実行環境数がゼロの間は時間課金が発生せず、実行環境数が1以上になっている間だけ課金される仕組みだ。コンテナイメージはSeekable OCI（SOCI）による遅延ロードやS3からの直接ストリーミングで起動時間を短縮できる。対応はAWSコンソール、CLI、SDK、CloudFormation、CDK、SAM、さらにKiroやClaude Code、Codexといったコーディングアシスタントからも設定可能という。ただし現時点ではWeb Functionsは非対応でEvent Functionsのみに限定され、TerraformやCloud Control系プロバイダーは`AcceleratorConfig`に未対応という制約も残る。AWSのシニアスペシャリストソリューションアーキテクトDaniel Abibは「OCIイメージを構築し、関数をそれに向けるだけで、プロビジョニングやスケーリング、イベント統合はLambdaが処理する。GPUドライバやCUDAバージョン、AMIを整合させる必要はなく、クラスタやデバイスプラグインを運用する必要もない」と述べている。一方で早期採用者からは、「イベントやキュー、他のAWSサービスの背後にモデルを置く」用途には適するが、ストリーミング応答や完全なサーバー制御が必要な場合はEC2上で直接vLLMを動かす方が良いとの指摘もあり、用途に応じた選択が求められそうだ。
