---
date: "2026-08-27T21:32:23+09:00"
title: "Intel、データセンターからエッジまでを貫くエージェントAI向け新アーキテクチャ3製品を発表"
description: "IntelがHot Chips 2026で、256コアXeon「Diamond Rapids」、推論特化GPU「Crescent Island」、エッジ向けSoC「Wildcat Lake」を発表し、エージェント型AIワークロードへの対応を進めた。"
tags:
  - AI
  - Other
references:
  - "https://newsroom.intel.com/client-computing/intel-outlines-architectures-for-agentic-ai-at-hot-chips-2026"
---

## 概要

Intelは8月24日、半導体アーキテクチャの祭典Hot Chips 2026において、エージェント型AI向けの新アーキテクチャ3種を発表した。データセンター向けXeonプロセッサ「Diamond Rapids」、推論処理に特化したGPU「Crescent Island」、クライアント・エッジ向けSoC「Wildcat Lake」の3製品で構成され、AIエージェントが自律的にタスクを遂行するワークロードをデータセンターからエッジデバイスまで一気通貫で支える製品ラインアップの刷新を打ち出した。Intel CTOのPushkar Ranade氏は「エージェント型AIは、トランジスタレベルからシステム全体まで、コンピュータ設計を根本的に変えている」と述べ、AIエージェントの普及がチップ設計思想そのものに影響を与えているとの認識を示した。

## Diamond Rapids ― 次世代エンタープライズXeon

次世代Xeonプロセッサ「Diamond Rapids」は、自社の最先端プロセスノードIntel 18A-Pを採用し、最大256コア、1.28GBのラストレベルキャッシュ(LLC)を搭載する。メモリは16チャネル構成で最大12800 MT/sの転送速度に対応し、I/O面ではPCIe Gen6を128レーン、CXL 3.0をサポートする。大規模なコア数と広帯域なメモリ・I/Oにより、エンタープライズ規模でのAI処理を見据えた設計となっている。

## Crescent Island ― 推論特化GPUとWildcat Lake ― エッジ向けSoC

推論処理に特化したGPU「Crescent Island」は、Xe3Pアーキテクチャを基盤に32基のXeコアと256基のXMXエンジンを搭載し、最大480GBのLPDDR5Xメモリを備える。消費電力は350ワットの空冷設計に収められており、リアルタイムでのAI推論処理の最適化を目指す製品と位置付けられている。一方、クライアント・エッジ向けSoC「Wildcat Lake」(Intel Core Series 3)は、パフォーマンスコア2基と効率コア4基の構成に、LPDDR5X-7467メモリ、Wi-Fi 7、Bluetooth 6.0を組み合わせ、エッジ環境でのAIエージェント実行を想定した設計となっている。

## 技術基盤と展望

これら3製品は、3Dパッケージング技術「Foveros Direct 3D」と、オープンなチップレット標準規格「UCIe」を共通の技術基盤としており、将来的な拡張性とチップレット間の相互運用性を重視した設計思想がうかがえる。データセンターの大規模推論から手元のエッジデバイスまで、AIエージェントが自律的に判断・実行するワークロードを支えるハードウェア基盤を段階的に整備する狙いがあり、AIエージェントの実用化が進む中でIntelが半導体設計の主導権を取り戻そうとする動きとして注目される。
