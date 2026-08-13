---
date: "2026-08-13T20:15:34+09:00"
title: "IBMとTogether AI、2.4億ドルでNvidia Blackwell搭載のAI推論クラスターを構築へ"
description: "IBMとTogether AIが、Nvidia Blackwell世代チップを用いたAI推論クラスターをIBM Cloud上に構築する2億4000万ドルの複数年契約を締結した。"
tags:
  - AI
  - Cloud
references:
  - "https://www.bnnbloomberg.ca/business/2026/08/11/ibm-together-ai-ink-240-million-deal-for-nvidia-powered-ai-inference-cluster/"
  - "https://siliconangle.com/2026/08/11/ibm-inks-240m-infrastructure-deal-ai-optimized-cloud-operator-together-ai/"
---

## 概要

IBMとAI最適化クラウドを手がけるスタートアップTogether AIは8月11日、Nvidia製Blackwell世代チップを活用したAI推論クラスターをIBM Cloud上に構築するため、総額2億4000万ドルの複数年契約を締結したと発表した。米国内に構築されるこのクラスターは、Nvidia HGX B300システム(Blackwell Ultra GPUを8基搭載)を中心に約2000基のBlackwell 300チップと、Nvidia Spectrum-Xネットワーキング機器で構成され、2027年前半にIBM Cloud経由で稼働開始する予定。用途はDeepSeekやMiniMaxといったオープンソースAIモデルの推論処理に特化しており、企業がプロプライエタリモデルより低コストで運用できる基盤を提供する狙いがある。

## 技術的な詳細

各HGX B300マザーボードはBlackwell Ultra GPUを8基搭載し、NVFP4形式で15ペタフロップスの性能を発揮する。サーバーは最低2TBのメモリと56コアCPUを2基備え、GPU間のデータ転送をNvidiaのConnectX-8 SuperNICが、外部トラフィックの制御をBlueField-3データ処理ユニットが担う構成となっている。Together AIは現在AWSなど他社インフラを借りて月間400兆トークンを処理するクラウドプラットフォームを運営しており、メディア生成向け最適化サービスやトークン課金制のProvisioned Throughput、サーバーレス、専用マシン、バッチ処理といった推論特化の5段階サービスティアを既に提供している。今回のIBMとの契約で得る計算資源は、これらサービスの提供拡大に充てられる計画だ。

## 背景と反響

Together AIはサンフランシスコを拠点に、企業がオープンモデルを低コストで運用できるプラットフォームを展開しており、2026年7月には80億3000万ドルの企業価値評価を受けたばかり。今回のIBMとの契約は、Nvidiaも出資した8億ドルの資金調達ラウンドから数週間後というタイミングでの発表となった。Together AIの最高収益責任者Kai Mak氏は「少なくとも2〜3カ月前には売り切れる見通しだ」と強い需要を示唆し、CEOのVipul Ved Prakash氏も「このクラスターにより、より多くの企業に本番運用レベルの推論をより速く提供できる。オープンソースAIを企業にとって当然の選択肢にするための大きな一歩だ」とコメントしている。

## 展望

今回の提携は、学習済みモデルを実際の応答生成に使う「推論」がクラウドコンピューティング需要の主要な牽引役になりつつあることを示す事例といえる。オープンソースモデルの低コスト運用を求める企業ニーズの高まりを受け、クラウド事業者やチップメーカー各社が推論特化インフラへの投資を加速させる動きが今後さらに広がる可能性がある。
