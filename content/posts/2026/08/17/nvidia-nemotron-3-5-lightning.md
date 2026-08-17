---
date: "2026-08-17T14:11:58+09:00"
title: "NVIDIA、軽量オープンMoEモデル「Nemotron 3.5 Lightning」とタスク振り分けツール「NeMo Switchyard」を発表"
description: "NVIDIAが300億パラメータ（アクティブ30億）のオープンMoEモデル「Nemotron 3.5 Lightning」と、エージェントタスクを最適なモデルへ振り分ける「NeMo Switchyard」を公開した。"
tags:
  - AI
references:
  - "https://www.cnbc.com/2026/08/11/nvidia-releases-nemotron-3point5-lightning-open-source-ai-model-.html"
  - "https://blogs.nvidia.com/blog/nemotron-lightning-switchyard-rtx-dgx/"
  - "https://www.marktechpost.com/2026/08/11/nvidia-ai-releases-nemotron-3-5-lightning-and-nemo-switchyard/"
---

## 概要

NVIDIAは8月11日、長期実行型のエージェントAIワークロード向けに設計された軽量なオープンソースMoE（混合専門家）モデル「Nemotron 3.5 Lightning」と、エージェントワークフロー内の各タスクを最適なモデルへ動的に振り分けるルーティングツール「NeMo Switchyard」を発表した。総パラメータ数は300億、実行時に活性化するアクティブパラメータは30億に抑えられており、コンシューマー向けGPUでも高速に動作するよう最適化されている。AIがチャットボットから自律的に動作するエージェントへとシフトする中で、AIの配置場所や進化のさせ方を自らコントロールしたいという企業ニーズに応える狙いがある。

## 技術的な詳細

Nemotron 3.5 Lightningは、高度に専門化されたタスクの実行に特化した設計が特徴で、NVIDIA公式ブログによると、同クラスの他モデルと比較して出力速度が最大4倍向上し、エージェントタスクの完了速度も30%高速化されているという。組み合わせて使われるNeMo Switchyardは、マルチエージェントシステム内の個々のタスクを性質に応じて適切なモデルへ振り分ける仕組みで、内部ベンチマークでは「フロンティアレベルの精度を維持しながら、タスク完了コストをOpus 4.8単体で処理する場合の約3分の1に削減できる」としている。モデルはNVIDIA NeMoを用いて組織固有のドメインデータで後学習（ファインチューニング）が可能で、ローカル環境での実行によるプライバシー制御にも対応する。

## 対応ハードウェアと展開範囲

Nemotron 3.5 Lightningは、NVIDIA RTX搭載PCやDGX Spark、DGX Station、そしてJetsonのようなエッジデバイスから、データセンターやクラウド環境まで幅広い環境での展開が可能とされている。軽量な設計により、これまで大規模なクラウド基盤を前提としがちだったエージェントAIを、ローカルやエッジ寄りの環境でも実用的な速度で動かせる点が強調されている。
