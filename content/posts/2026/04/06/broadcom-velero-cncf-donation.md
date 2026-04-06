---
date: "2026-04-06T10:38:47+09:00"
title: "BroadcomがVeleroをCNCFサンドボックスに寄贈、Kubernetesバックアップのベンダーニュートラルな発展へ"
description: "BroadcomはKubeCon EU 2026にて、Kubernetesネイティブのバックアップ・リストアツール「Velero」をCNCFサンドボックスに寄贈し、コミュニティ主導のガバナンスと長期的な持続可能性を強化した。"
tags:
  - Cloud
  - OSS
references:
  - "https://thenewstack.io/broadcom-donates-velero-cncf/"
  - "https://thenewstack.io/broadcom-velero-cncf-kubernetes/"
  - "https://www.techzine.eu/news/infrastructure/139783/broadcom-ships-vks-3-6-and-moves-velero-to-cncf-sandbox/"
  - "https://news.broadcom.com/news/2026-kubernetes-ecosystem"
---

## 概要

BroadcomはKubeCon EU 2026（アムステルダム）にて、Kubernetesネイティブのバックアップ・リストア・移行ツール「Velero」をCloud Native Computing Foundation（CNCF）のサンドボックスプロジェクトとして寄贈すると発表した。Veleroは2026年2月にCNCFサンドボックスへの申請が受理されており、今回のKubeConでの発表はその公式なコミュニティへの移行を示すものとなった。CNCF CTOのChris Aniszczyk氏は「VeleroはKubernetes環境における重要なバックアップおよびディザスタリカバリレイヤーを提供し、ステートフルアプリケーションを保護します。CNCFサンドボックスに参加することで、ベンダーニュートラルな環境のもとコミュニティコラボレーションを促進できます」とコメントした。

## VeleroのCNCF移行の背景と意義

Veleroはクラスタの状態と永続データの保護、ディザスタリカバリおよびロールバックワークフロー、クラスタ間や異なるクラウド・オンプレミス環境へのワークロード移行といった機能を提供するKubernetesエコシステムにおける重要なツールだ。これまでBroadcom（旧VMware）が主体的に開発・管理してきたが、CNCFへの移管によってベンダーニュートラルなガバナンスのもとに置かれることになる。これにより、特定ベンダーへの依存という懸念が払拭され、幅広いコントリビューターが参加しやすくなる。Broadcomは自社がCNCFのトップ5コントリビューターに位置すると主張しており、今回の寄贈はオープンソースコミュニティへのコミットメントの一環として位置づけられている。

## 同時発表：VMware vSphere Kubernetes Service 3.6

Veleroの寄贈と合わせ、BroadcomはVMware vSphere Kubernetes Service（VKS）3.6もリリースした。主な新機能として、Kubernetes 1.35への対応（24ヶ月の拡張サポート付きでCNCF認定済み）、RHEL 9のサポート追加（既存のPhoton OS 5、Ubuntu 22.04/24.04、Windows Server 2022に加え）、ノードプール単位で異なるOSを組み合わせられるヘテロジニアスクラスタ対応が挙げられる。運用面では、データベースやレイテンシ敏感型ワークロード向けのTuneDプロファイルによるカーネル・sysctlチューニング、アップグレード前の事前チェック機能（SystemCheckSucceeded条件）、vCenter認証不要でのサポートバンドル生成が実装された。セキュリティ面ではAppArmorプロファイルのカスタムリソース管理やnftablesバックエンドのサポートも追加されている。

## 今後の展望

BroadcomはCNCFへのVelero移管を通じ、エンタープライズ向けKubernetesデータ保護の長期的な持続可能性を高めるとともに、より広いコミュニティと共同でプロジェクトの技術的方向性を決定していく方針だ。VKS 3.6とVeleroのCNCF移管は、BroadcomがVMware Cloud Foundation上でVMとコンテナを対等なワークロードとして扱うという戦略的方向性とも一致しており、エンタープライズKubernetesプラットフォームの信頼性と中立性をアピールする動きとして注目される。
