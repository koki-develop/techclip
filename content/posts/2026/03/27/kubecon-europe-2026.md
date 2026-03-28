---
date: "2026-03-27"
title: "KubeCon Europe 2026で注目されたeBPF・mTLS統合とAI推論基盤の進化"
description: "アムステルダムで開催されたKubeCon Europe 2026において、CiliumによるサイドカーレスmTLS、AI推論ワークロード向けスケジューリング、BSD統合など、Kubernetesエコシステムの成熟を示す多数の発表が行われた。"
tags:
  - Cloud
references:
  - "https://opensource.microsoft.com/blog/2026/03/24/whats-new-with-microsoft-in-open-source-and-kubernetes-at-kubecon-cloudnativecon-europe-2026/"
  - "https://www.heise.de/en/news/KubeCon-EU-2026-Kubernetes-Matures-BSD-eBPF-and-mTLS-11227348.html"
  - "https://cloud.google.com/blog/products/containers-kubernetes/gke-and-oss-innovation-at-kubecon-eu-2026"
---

## 概要

2026年3月24日から26日にかけてアムステルダムで開催されたKubeCon + CloudNativeCon Europe 2026には、13,000人以上が参加した。誕生から12年を迎えたKubernetesは成熟期に入り、今年のカンファレンスではeBPFとmTLSによるネットワークセキュリティの強化、AI推論ワークロードへの対応、そしてBSD統合による実行環境の多様化が主要テーマとして浮上した。MicrosoftのBrendan Burns氏（Corporate Vice President兼Technical Fellow）は、AIインフラにおける課題が「動作するか壊れるか」から「良い結果か悪い結果か」へと根本的に変化していると指摘し、Kubernetesの運用成熟度を現代のワークロードに適用することの重要性を強調した。

## サイドカーレスmTLSの実現：CiliumとeBPFの統合

今回のKubeConで最も注目を集めた技術トピックの一つが、Cilium v1.19以降で実現されたサイドカープロキシ不要のmTLS（相互TLS認証）である。従来のサービスメッシュではサイドカーコンテナが必要だったが、新しいアプローチではeBPF（Extended Berkeley Packet Filter）とIstioのztunnel（Rust実装のコンポーネント）を組み合わせ、各ノード上の軽量プロキシがTLS処理を担う「アンビエントモード」を採用している。設定はCilium Helm chartでztunnel機能を有効化し、ネームスペースに`io.cilium/mtls-enabled=true`ラベルを適用するだけの3ステップで完了する。この方式はノード単位ではなくセッション単位の認証を実現し、ハンドシェイク時のパケットロスも解消されている。

Microsoftはこの技術をAzure Kubernetes Service（AKS）にも統合し、「Azure Kubernetes Application Network」としてフルサービスメッシュのオーバーヘッドなしにmTLS、アプリケーション対応の認可、トラフィックテレメトリを提供する。さらにWireGuardによるノード間暗号化やCilium Cluster Meshによるクロスクラスタネットワーキングも発表された。

## AI推論基盤とスケジューリングの進化

AI関連では、Dynamic Resource Allocation（DRA）がKubernetesで正式にGA（一般提供）となり、Kubernetes 1.36ではWorkload APIにDRAサポートが追加された。Microsoftは新たなオープンソースプロジェクト「AI Runway」を発表し、推論ワークロード向けのKubernetes APIとWebインターフェース、HuggingFace統合、GPUメモリ適合インジケーターを提供する。AKSにおいてもGPUメトリクスのPrometheus/Grafana統合や、自然言語によるネットワーク診断クエリ機能「Agentic Container Networking」が追加された。CNCFサンドボックスプロジェクトの「HolmesGPT」はエージェント型のトラブルシューティングツールとして紹介された。

## BSD統合と新しいコンテナランタイム

Kubernetesエコシステムの実行環境も多様化が進んでいる。CNCFメンバーであるProject Limaはバージョン2.1をリリースし、macOSに加えFreeBSDをゲストOSとしてサポートした（実験段階）。K3s、k0s、RKE2と互換性があり、コンテナに匹敵する軽量な仮想マシンを実現する。また、CNCFに約1年前に加入したProject uruncは、ユニカーネルコンセプトを採用した新しいコンテナランタイムで、BSDアプリケーションをLinuxコンテナ向けに移植することなく、隔離された環境で実行可能にする。

## 運用成熟度の向上と今後の展望

AKSでは運用面の改善も多数発表された。ブルーグリーン方式のエージェントプールアップグレード、エージェントプールのロールバック機能（フル再構築なしに前バージョンへ復帰可能）、プリロード済みコンテナと設定を含むカスタムノードイメージ仕様「Prepared Image Specification」、そしてローカル開発環境「AKS Desktop」のGA化などが含まれる。一方で、ヨーロッパの参加者にとって重要なデータ主権の問題については議論が限定的だったとの指摘もあり、今後のカンファレンスでの課題として残された。次回のKubeCon Europeは2027年にバルセロナ、2028年にベルリンで開催される予定である。
