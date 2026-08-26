---
date: "2026-08-26T14:09:12+09:00"
title: "Kubernetes 1.37リリース、9年目のMetrics APIがついにGAへ"
description: "Kubernetes 1.37が正式リリースされ、長年ベータ版だったMetrics APIがGAに到達したほか、KYAMLやDRAの機能強化を含む16件が安定版に昇格した。"
tags:
  - Cloud
  - OSS
references:
  - "https://www.kubernetes.dev/resources/release/"
---

## 概要

Kubernetesプロジェクトは8月26日、最新版となる「Kubernetes 1.37」を正式リリースした。今回の目玉は、実に9年近くベータ版のまま据え置かれていたMetrics API（metrics.k8s.io）がついに安定版（GA）へ到達したことだ。同APIは2017年3月にAlphaとして導入され、同年9月にBetaへ昇格して以降、Horizontal Pod Autoscaler（HPA）や`kubectl top`コマンドなど、実運用で広く使われながらも長らくベータのステータスにとどまっていた。スキーマ自体はほとんど変更されておらず、安定した実績を踏まえて今回ようやく正式に昇格した形だ。なお新しい`v1`と既存の`v1beta1`はAPIの見た目上は同一で、移行は非破壊的に行われ、`v1beta1`は今後のリリースで段階的に廃止される予定となっている。

Kubernetes 1.37全体では、KYAMLの出力サポートやPodレベルのリソース管理、DRA（Dynamic Resource Allocation）関連の機能強化など、合計16件のエンハンスメントが安定版に昇格した。これらを含め、Alpha・Beta・Stableの各段階への昇格を合わせると28件の変更が今回のリリースに盛り込まれている。

## 技術的な詳細

安定版に到達した主な機能としては、`kubectl`向けの新しい出力形式「KYAML」が挙げられる。KYAMLはマップを波括弧`{}`、リストを角括弧`[]`で表現することで、インデントの解釈違いなどYAML特有の落とし穴（いわゆる「ノルウェー問題」）を解消する標準フォーマットとして安定版入りした。また、コンテナ間でCPU・メモリ・hugepageのリソースプールを共有できる「Pod-level resources」も安定版に昇格している。

DRA関連では、ハードウェア障害時の扱いを制御する「デバイスレベルのtaintとtoleration」がGAに到達したほか、NUMAノードのトポロジー情報を標準的に公開する`resource.kubernetes.io/numaNode`属性の導入、ドライバー固有の状態情報を扱う「Resource Claim Status」の安定化、DRAのメタデータをDownward API経由でワークロードに公開する機能のBeta昇格など、ハードウェアリソースのきめ細かな管理に向けた改善が進んだ。このほか、SELinuxマウントの最適化が安定版に昇格し、コンテナ単位のulimit設定がAlpha機能として新たに追加されている。

## 非推奨化と廃止の動き

今回のリリースでは複数の機能で非推奨化・段階的廃止が進められた。`kubectl run`コマンドの`--filename`/`-f`フラグは、生成されるPodがCLI引数のみから構築される設計であることを理由に非推奨となった。また、Static PodがSecretやConfigMapを直接参照することも禁止される。Static PodはAPI経由で作成されないため、こうしたAPIリソースへの直接参照は本来の設計外だったための対応だ。

kube-proxyのIPVSモードについても、多リリースにわたる段階的な非推奨化が始まった。1.37では非推奨の警告ログが出力されるようになり、1.40でデフォルト無効化、1.43で完全削除される計画が示されている。背景にはIPVSがKubernetes Servicesの実装を完全にはカバーしておらず、内部的にiptablesへの依存が残っていることがある。並行してkube-proxyのデフォルトをNFTablesへ移行する動きも進んでおり、1.37ではその移行に向けた警告が出始めている。さらに、cgroup v1のサポート廃止に向けた動きも継続しており、1.35以降kubeletの設定で`failCgroupV1`がデフォルトで有効になっているため、明示的な設定なしにcgroup v1に依存するノードはkubeletの起動に失敗するようになっている。

## 今後の展望

Metrics APIのGA到達は、長年ベータのまま実運用を支えてきたコンポーネントに正式な安定性の裏付けが与えられたという意味で象徴的な出来事だ。一方で、IPVSモードやcgroup v1、`kubectl run -f`など複数の機能が今後複数リリースにわたって段階的に姿を消していく方針が示されており、運用者にはNFTablesやcgroup v2への移行、CLIスクリプトの見直しなど、計画的な対応が求められることになる。
