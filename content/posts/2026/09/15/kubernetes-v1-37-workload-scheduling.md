---
date: "2026-09-15T18:14:18+09:00"
title: "Kubernetes v1.37リリース、AI/MLワークロード向けギャングスケジューリングがベータへ 階層スケジューリングのCompositePodGroupも登場"
description: "Kubernetes v1.37がリリースされ、AI/MLやバッチ処理を意識したワークロード対応スケジューリング機能群がベータに到達し、階層的なグループ管理を行う新API CompositePodGroupもアルファで追加された。"
tags:
  - Cloud
references:
  - "https://kubernetes.io/blog/2026/09/08/kubernetes-v1-37-advancing-workload-aware-scheduling/"
  - "https://www.fairwinds.com/blog/kubernetes-1.37-is-here-pod-rightsizing-dra-and-gang-scheduling"
  - "https://thenewstack.io/kubecon-kubernetes-updates-security/"
---

## 概要

Kubernetes v1.37が8月26日にリリースされた。今回のリリースは67件の機能強化を含み、うち16件が安定版(Stable)に到達した大型アップデートとなっている。特に目を引くのが、AI/MLトレーニングや大規模バッチ処理を意識した「ワークロード対応スケジューリング(Workload-Aware Scheduling)」領域の進化だ。複数のPodをまとめて同時起動させる「ギャングスケジューリング」を支えるWorkload APIとPodGroup APIがベータに昇格したほか、ワークロード全体の完了状況を踏まえてプリエンプションを判断するWorkload-Aware Preemption(WAP)、PodGroup間でGPUなどの専用リソースを共有できるShared DRA ResourceClaimsも同じくベータへ進んだ。さらに、階層的なグループ管理を可能にする新API「CompositePodGroup」がアルファとして新設された。

## ギャングスケジューリングとワークロード対応API

ギャングスケジューリングは、分散深層学習や密結合なバッチ処理ワークロードのように、互いに依存し合う複数のPodが「全員揃わない限り意味を成さない」ケースのために設計された仕組みだ。従来のPod単位スケジューリングでは、一部のPodだけがノードに配置され残りがリソース不足で待たされる「部分割り当てによるロックアップ」が発生しやすかったが、PodGroup APIは指定したメンバー数が揃うまでスケジュール開始自体を待機させることで、これを防ぐ。この機能は1.35でアルファ導入された後、1.36でWorkload APIとPodGroup APIに分割され、v1.37で両者が統一の機能ゲートのもとv1beta1に昇格した。なお1.36で作成したv1alpha2マニフェストはv1.37では非対応となるため、アップグレード前に削除しておく必要がある点は運用者にとって注意点だ。新設のCompositePodGroup APIは、複数レベルのトポロジー制約を持つ異種混合のPodグループを階層的に表現できるようにするもので、JobSetやLeaderWorkerSet(LWS)といった上位層のワークロードAPIをネイティブにサポートする土台となる。

## Pod Rightsizing・DRAなど関連機能の成熟

Pod再起動なしにCPU/メモリを調整できる「Pod Rightsizing(In-Place Pod Resize)」も前進し、v1.37ではInitコンテナのリサイズ対応がGAに到達、kubelet側でリソースをまとめて管理するPod-Level Resource Managersがベータに昇格したほか、メモリバックアップボリュームのリサイズ機能がアルファで追加された。この機能はcgroup v2を前提とするため、cgroup v1の廃止を後押しする流れも加速している。GPUなど専用ハードウェアの柔軟な割り当てを担うDynamic Resource Allocation(DRA)も、2025年のコアAPI GA、2026年のデバイス分割・キャパシティ管理・障害検知機能のベータ昇格を経て、v1.37ではデバイスのテイント/トレラント機能と状態レポート機能がGAに到達した。これにより、マルチGPUノード全体を切り離すことなく、劣化した個別GPUだけを隔離してクラスタ容量を最大化できるようになる。

## 運用者への影響と展望

これらの新機能はいずれもオプトイン方式であり、既存のPod単位スケジューリングは従来通り動作するため、アップグレードによる直接的な破壊的変更は少ない見込みだ。JobSetやLWSを利用しているユーザーは自動的に恩恵を受けられる一方、独自のワークロードコントローラーを実装している場合は新設のController Integration APIへの移行が推奨される。このほかv1.37ではMemory QoSやNative Histogramsのベータ昇格、Metrics APIの安定版到達なども含まれており、Kubernetesが引き続きAI/MLおよびHPC領域でのエンタープライズ利用を強く意識した方向に進化していることがうかがえる。
