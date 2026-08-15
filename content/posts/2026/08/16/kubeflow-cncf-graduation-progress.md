---
date: "2026-08-16T02:03:30+09:00"
title: "KubeflowがCNCF卒業目前に、Kale 2.0・Trainer・Notebooks v2など新機能を一挙発表"
description: "MLプラットフォームKubeflowがCNCF卒業間近と伝えられ、Kale 2.0やKubeflow Trainer、宣言型のNotebooks v2、Kubernetes 1.34対応のCommunity Distribution 26.03を発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://www.infoq.com/news/2026/08/kubeflow/"
---

## 概要

Kubernetes上でMLワークフローを構築・運用するためのプラットフォームであるKubeflowが、CNCF（Cloud Native Computing Foundation）の卒業（Graduation）に向けて急速に前進していることが明らかになった。卒業はCNCFホスティングプロジェクトの中でも最も成熟した段階に位置づけられるステータスであり、Kubeflowが本番環境で広く使われる、安定したMLエコシステムへと進化したことを示す節目となる。これに合わせて、Kale 2.0、Kubeflow Trainer、新設計のNotebooks v2、そしてKubernetes 1.34以降に正式対応したKubeflow Community Distribution 26.03など、複数の新機能・新コンポーネントがまとめて発表された。

## Kale 2.0とKubeflow Trainer

Kale 2.0は、注釈を付けたJupyterノートブックを本番運用可能なパイプラインへと自動変換するツールで、KFP（Kubeflow Pipelines）SDKのコードを一切書かずに変換できる点が特徴だ。Kubeflow Pipelines v2アーキテクチャにも対応しており、データサイエンティストが実験段階のノートブックから本番運用への移行をスムーズに進められるよう設計されている。

一方のKubeflow Trainerは、MPI（Message Passing Interface）サポートを通じて分散AIトレーニングとHPC（高性能コンピューティング）ワークロードを統一的に扱えるコンポーネントとして刷新された。特にFlux Frameworkとの正式統合により、単一のKubernetes環境上で大規模なHPCシミュレーションとAIトレーニングを並行して実行できるようになった点が注目されている。LinkedIn上の投稿では、この統合は「HPC技術のクラウドネイティブインフラ採用に向けた重要な一歩」であり、「現代的なGenAIワークロードに不可欠」だと評価されている。

## Notebooks v2とKubernetesエコシステムへの統合

完全に再設計されたNotebooks v2は、宣言型のCRD（Custom Resource Definition）駆動アーキテクチャを採用した点が大きな変更点だ。これによりプラットフォームチームは、JupyterLabやVS Codeといったインタラクティブな開発環境に対して、テンプレート化された形で制御・管理を行えるようになる。現在はalpha版として利用可能だが、Kubeflowプロジェクト全体が宣言的でKubernetesネイティブな設計思想へと寄せていく方向性を示すものといえる。

さらに、Kubeflow Community Distribution 26.03ではKubernetes 1.34以降への正式な検証が完了した。マルチテナント対応の強化やPod Security Standards Restrictedポリシーへの互換性実装が盛り込まれ、組織規模での運用における信頼性とセキュリティの向上が図られている。

## 背景と今後の見通し

Kubernetesは今やプロダクション環境におけるAI基盤の中核レイヤーになりつつあり、実運用の事例も蓄積されてきている。記事ではSubaru Corporationの事例が紹介されており、KubernetesとArgo CDを活用することで30GB以上に及ぶAIコンテナイメージのプル時間を3時間から3分にまで短縮したという。

コミュニティ面では、新たなアウトリーチプログラムやML Experienceワーキンググループの発足により、Kubeflowへの参加障壁を下げる取り組みも進んでいる。8月19日には実世界のMLOpsユースケースを紹介する仮想ショーケースイベントの開催も予定されており、今回発表された各コンポーネントの実運用への浸透が今後の焦点となりそうだ。
