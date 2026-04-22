---
date: "2026-04-22T18:29:39+09:00"
title: "Kubernetes v1.36リリース — 80件のエンハンスメント、User Namespaces GA・HPAゼロスケールがベータ昇格"
description: "Kubernetes v1.36が2026年4月22日にリリース。80件のエンハンスメントを含み、User Namespacesの安定化、HPAのゼロスケール対応（ベータ昇格）、OCI VolumeSource GA、Ingress-NGINXの廃止などが主要なトピックとなっている。"
tags:
  - Cloud
  - OSS
references:
  - "https://kubernetes.io/blog/2026/03/30/kubernetes-v1-36-sneak-peek/"
  - "https://www.perfectscale.io/blog/kubernetes-v1-36-sneak-peek"
  - "https://palark.com/blog/kubernetes-1-36-release-features/"
---

## 概要

Kubernetes v1.36が2026年4月22日に正式リリースされた。今回のリリースは80件のエンハンスメントを含む大型アップデートで、安定版（GA）昇格が18件、ベータ昇格が18件、新規アルファ機能が26件という構成となっている。コンテナセキュリティの強化、GPU・アクセラレータ管理の改善、オートスケーリングの柔軟性向上が主要テーマだ。

## 主要なGA（安定版）機能

**User Namespaces in Pods** がついにGA（安定版）に昇格した。v1.25でのアルファ導入から約4年を経ての安定化となる。この機能はコンテナ内のroot（UID 0）を非特権ホストユーザーにマッピングすることでセキュリティ隔離を実現するもので、Podスペックに `hostUsers: false` を指定するだけで有効化できる。

**Mutating Admission Policies** もGAに昇格した。CELベースのミューテーションを外部Webhookサーバーなしでkubernetes本体に統合でき、インフラオーバーヘッドと単一障害点の排除を実現する。

**OCI VolumeSource** のGA昇格も重要な変更だ。OCIイメージをボリュームとしてマウントできるようになり、モデルウェイトや設定ファイル、データセットをアプリケーションコンテナとは独立して配布できる。AIモデルのデプロイにおいて有用な機能となる。

このほかにも **外部ServiceAccountトークン署名**（HSMやクラウドKMSへの署名委譲）、**DRA向けKubeletPodResources API**（GPUなどのリソースをgRPC経由でpod単位に照会）、**SELinuxラベル変更の高速化**（ファイル単位の再ラベリングからマウント時の一括適用へ）がGAに昇格している。

## 注目のベータ機能：HPA Scale to Zero

**HPA（Horizontal Pod Autoscaler）のゼロスケール対応** が待望のベータ昇格を果たし、デフォルト有効化された。2019年のv1.16でアルファ導入されてから実に7年越しの昇格となる。アイドル時にDeploymentのレプリカ数をゼロまでスケールダウンできるため、コスト削減に直結する機能だ。

また、**DRAのパーティショナブルデバイスサポート**（ベータ）により、NVIDIAのMIG（Multi-Instance GPU）のような分割可能なGPUをスケジューリング時に動的に分割できるようになった。従来の静的な事前設定から脱却し、より柔軟なGPUリソース管理が可能になる。

## 新規アルファ機能

26件の新規アルファ機能の中で特筆すべきものをいくつか挙げる。

**Workload-aware Preemption** は分散トレーニングなど、複数のPodが同時にリソースを必要とするワークロードを対象に、Podグループを単一エンティティとして扱うプリエンプション制御を実現する。一部のPodだけがプリエンプトされて処理が中断するような問題を防ぐ。

**HPA External Metrics Fallback** は、外部メトリクスソースが一時的に障害を起こした際にフォールバック値を使ってオートスケーリングを継続できるようにするものだ。

**PVC Last-Used Tracking** は `status.lastUsedTime` フィールドを追加して孤立した永続ストレージボリュームの特定を容易にする。

スケーラビリティ面では **Server-side Sharding**（クライアントが `shardSelector` パラメーターで特定データシャードにサブスクライブ）、**Graceful Leader Transition**（コントロールプレーンコンポーネントのプロセス再起動なしのリーダー移行）、**Native Histogram Support**（Prometheusネイティブヒストグラム対応）なども追加された。

## 廃止・削除と移行推奨事項

**gitRepoボリュームプラグイン** が完全削除された。v1.11から廃止されていたが、今回ついに削除となる。rootコード実行の可能性があるセキュリティ脆弱性が理由で、init containersや外部のgit-syncツールへの移行が推奨される。

**IPVS mode in kube-proxy** も削除対象となっている。

**externalIPsフィールド**（Service spec）がv1.36で廃止予定となった（完全削除はv1.43予定）。CVE-2020-8554に関連するMITM攻撃リスクが理由で、LoadBalancer ServicesやGateway APIへの移行が推奨される。

また、**Ingress-NGINX** は2026年3月24日にSIG NetworkおよびSecurity Response Committeeによって正式に廃止宣言された。既存環境での継続動作やHelmチャート・コンテナイメージは引き続き利用可能だが、セキュリティアップデートやバグ修正は提供されなくなった。Gateway APIへの移行が強く推奨されている。
