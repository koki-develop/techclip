---
date: "2026-03-29"
title: "TektonがCNCF Incubatingに昇格、KubernetesネイティブCI/CDの標準基盤として成熟を証明"
description: "CNCFの技術監視委員会がCI/CDフレームワークTektonをIncubatingプロジェクトに昇格させ、クラウドネイティブエコシステムにおける成熟度と重要性を正式に認定した。"
tags:
  - Cloud
  - OSS
references:
  - "https://www.cncf.io/blog/2026/03/24/tekton-becomes-a-cncf-incubating-project/"
---

## 昇格の概要

CNCF（Cloud Native Computing Foundation）の技術監視委員会（TOC）は2026年3月24日、KubernetesネイティブのCI/CDフレームワーク「Tekton」をIncubatingプロジェクトとして正式に承認した。TektonはCD Foundation（CDF）で既に卒業プロジェクトとしての地位を確立しており、CNCFにはSandboxを経ずに直接Incubatingレベルで受け入れられた。これはプロジェクトの成熟度、安定性、そしてクラウドネイティブエコシステムにおける重要性が認められた結果である。TOCスポンサーのChad Beaudin氏は「TektonはKubernetesネイティブなデリバリーのためのコアインフラとしての実力を証明した。Incubatingへの移行は、強力なマルチベンダーガバナンスとCNCFプロジェクトとの深い連携を反映している」と評価している。

## Tektonのアーキテクチャと主要コンポーネント

TektonはKubernetes上で動作するCI/CDフレームワークであり、Steps、Tasks、Pipelinesという構成可能なプリミティブを通じて、マルチクラウドおよびオンプレミス環境でのビルド、テスト、デプロイを実現する。プロジェクトは複数のコンポーネントで構成されており、CI/CDワークフローの中核を担う「Pipelines」（コアはv1.0安定版に到達済み）、Gitプッシュやプルリクエストなどのイベントに基づいてパイプラインを起動する「Triggers」、コマンドラインインターフェースの「CLI」、Webベースの管理UIである「Dashboard」、そしてアーティファクトの署名・証明を行うサプライチェーンセキュリティツール「Chains」がある。

## コミュニティの成長と採用実績

Tektonのコミュニティは着実に成長を遂げており、GitHub上で11,000以上のスター、5,000以上のプルリクエスト、2,500以上のIssue、そして600人以上のコントリビューターを擁する。企業採用も広がっており、Red Hat OpenShift PipelinesやIBM Cloud Continuous Deliveryといった商用製品の基盤として活用されているほか、Puppet社やFord Motor Companyなどの大手企業でも導入されている。さらに、CNCFプロジェクトであるShipwrightやRed Hatが主導するKonfluxといったプロジェクトの基盤としても機能しており、エコシステム内での存在感を高めている。Argo CD（GitOps）、SPIFFE/SPIRE（アイデンティティ管理）、Sigstore（署名・検証）との統合も進んでいる。

## 今後のロードマップ

Tektonの今後の開発では、サプライチェーンセキュリティの強化が重要な柱となる。SLSA Level 3をデフォルトで達成することを目指すほか、共有ストレージなしでタスク間のデータを安全に受け渡す「Trusted Artifacts」機能の開発が進められている。また、リモートのTask/Pipeline参照の構文改善、Kueueとの統合による高度なスケジューリング、長期的な履歴管理とクエリのためのResults APIの安定化、Artifact Hubを通じたCatalogの進化、そしてGitベースのワークフローを実現する「Pipelines as Code」の継続的な開発が予定されている。TOCスポンサーのJeremy Rickard氏は「Tektonのコンポーザブルな設計と幅広い採用は、クラウドネイティブワークフロー環境において重要な位置を占めている」と述べており、Incubating昇格によりエンタープライズ採用のさらなる加速が期待される。
