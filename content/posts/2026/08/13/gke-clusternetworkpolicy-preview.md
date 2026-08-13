---
date: "2026-08-13T14:30:23+09:00"
title: "GKEで「ClusterNetworkPolicy」がプレビュー提供、階層構造でクラスタ全体のセキュリティを強制"
description: "GoogleがGKEにクラスタ全体を対象とするネットワークポリシー標準ClusterNetworkPolicyをプレビュー提供し、管理者・開発者・ベースラインの3層でトラフィック制御を一元的かつ決定論的に強制できるようにした。"
tags:
  - Cloud
references:
  - "https://cloud.google.com/blog/products/networking/new-clusternetworkpolicy-in-gke"
---

## 概要

Googleは2026年8月10日、Google Kubernetes Engine(GKE)向けに「ClusterNetworkPolicy(CNP)」のプレビュー提供を開始した。CNPはKubernetes SIG-Network(SIG-Policy Working Group)が策定したオープンソースのAPI仕様で、従来の名前空間単位の`NetworkPolicy`とは異なり、クラスタ全体を対象にネットワークトラフィックを制御できる。GKE 1.36以降で利用可能。決済処理など機密ワークロードを扱う名前空間の隔離や、kube-dnsのような重要な内部サービスの保護を、開発者側の設定に左右されず一貫して強制できる点が特徴だ。プロプライエタリな独自拡張ではなく、Kubernetesコミュニティおよび実装パートナーであるCiliumコミュニティと協調して設計されており、異なる環境間でもポリシー設定を再利用できるポータビリティを備える。

## 技術的な詳細

CNPの中核は、**Admin Tier(管理者層)**・**Network Policy Tier(ネットワークポリシー層)**・**Baseline Tier(ベースライン層)**という3層構造による階層的なポリシー評価にある。評価はAdmin Tierから順に行われ、最上位のAdmin Tierは他のすべてのポリシーに優先し、バイパス不可能なコンプライアンス・セキュリティ要件をRBACで厳格に強制する。中間のNetwork Policy Tierは従来通り開発者がアプリケーション固有のポリシーを名前空間内で定義する層で、Admin Tierのルールには従属する。最下層のBaseline Tierはクラスタ全体のデフォルト動作(例えばゼロトラストに基づく「Deny All」)を設定し、名前空間スコープのポリシーによって上書き可能となっている。この階層構造により、従来のNetworkPolicyで起こり得た平坦な構造ゆえの設定競合を排除し、決定論的な評価を実現している。

Admin Tierのルールは`Accept`(トラフィックを明示的に許可)、`Deny`(明示的に拒否)に加え、新たに`Pass`という第3のアクションをサポートする。Passはトラフィックの最終的な許可・拒否の判断を下位層、すなわち開発者の名前空間ポリシーに委譲する仕組みで、セキュリティチームがグローバルルールでトラフィックを検査しつつ、最終決定は開発者側に委ねるといった柔軟な運用を可能にする。APIは`policy.networking.k8s.io/v1alpha2`というAPIグループで提供され、名前空間スコープの標準`NetworkPolicy`(`networking.k8s.io`)とは別のリソースとして区別される。マニフェストでは`tier`(Admin/NetworkPolicy/Baseline)、`priority`(同一層内の優先度)、`subject`(対象となるPodや名前空間のセレクタ)、`ingress`/`egress`ルールなどを指定する。

具体的なユースケースとしては、決済処理や規制対象データを扱う名前空間へのアクセスをAdmin Tierで一括してDenyし、開発者側の許可設定では上書きできないようにする「機密ワークロードの隔離」、kube-dnsなど内部運用上重要なサービスへのアクセスをAdmin TierのAcceptルールで維持し、名前空間ポリギーの誤設定の影響を受けないようにする「コアサービスの保護」、そしてIPアドレス範囲(IPv4の`0.0.0.0/0`やIPv6の`::/0`など)を用いたegressトラフィックの制御による不正なデータ流出防止が挙げられている。利用にはGKE 1.36以降のクラスタが必要で、現時点ではプレビュー機能として提供されている。
