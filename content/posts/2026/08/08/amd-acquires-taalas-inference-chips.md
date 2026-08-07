---
date: "2026-08-08T08:09:45+09:00"
title: "AMD、モデル重みをシリコンに焼き込むTaalasを買収 推論特化チップでNvidiaに対抗"
description: "AMDがAIモデルの重みを直接シリコンに刻み込む推論チップスタートアップTaalasを買収し、Nvidia対抗の推論ハードウェア戦略を強化する。"
tags:
  - AI
  - Other
references:
  - "https://www.theregister.com/systems/2026/08/06/amd-acquires-ai-chip-startup-taalas-to-boost-inference-performance-by-etching-models-into-silicon/5284344"
  - "https://ir.amd.com/news-events/press-releases/detail/1296/amd-acquires-taalas-to-advance-compute-solutions-for-rapidly-growing-ai-inference-market"
  - "https://www.cnbc.com/2026/08/06/amd-buys-taalas-startup-that-hardwires-ai-models-into-its-silicon.html"
---

## 概要

AMDは2026年8月6日、カナダ・トロント拠点のAI推論チップスタートアップTaalasの買収に合意したと発表した。買収額は非公表で、取引は規制当局の承認を経て2026年第4四半期に完了する見込みという。Taalasは、AIモデルの重みを汎用メモリに読み込むのではなく、シリコンチップに直接焼き込むという独自のアプローチで推論処理を高速化する技術を持つ。AMD人工知能グループの上級副社長Vamsi Boppana氏は、顧客が用途に応じて最適な計算ソリューションを柔軟に選べるようにするという同社の戦略の一環だと位置づけている。Taalas共同創業者兼CEOのLjubisa Bajic氏も、AMDの規模とリソースを得ることで「モデル中心のハードウェア設計」というアプローチのグローバル展開を加速できると期待を示した。

## 技術的な詳細

Taalasのチップは「Model-Specific Integrated Circuits（MSIC）」と呼ばれるアーキテクチャを採用し、HBMのような外部メモリに依存する従来のGPU設計とは根本的に異なる構造を持つ。チップ内部は、モデルの重みを格納するマスクROMの「recall fabric」と、KVキャッシュや微調整用アダプタを扱うSRAM fabricの2領域で構成される。TSMCの6nmプロセスで製造された試作チップ「HC1」は、Meta社のLlama 3.1 8Bモデルにおいて1ユーザーあたり毎秒16,960トークンという速度を達成しており、2月の発表時点でNvidia製GPU比48倍の速度だったとされる。次世代の「HC2」は200億パラメータ規模のモデルに対応し、1兆パラメータ級のモデルを扱うには50チップが必要になる見込みだ。一方で最大の弱点は柔軟性の欠如で、一度製造したチップは特定のモデル専用となり、大幅なモデル変更には再製造が必要になる。ただしTaalasは、更新の際に変更が必要なのは「配線層2層のみ」であり、フルスクラッチでの再設計に比べコストを抑えられると説明している。

## 背景と今後の展望

この買収の狙いは、AIエージェントやコーディング支援ツールなど、高速な推論性能が求められるプレミアム推論サービス市場でのシェア獲得にある。Taalasの技術は、AMDのラックスケールシステム「Helios」やInstinct GPU、EPYC CPU、ROCmソフトウェアといった既存のAIプラットフォーム全体に統合される計画で、プロンプト処理をGPUが担い、トークン生成をTaalasのアクセラレータが担う、といった役割分担型の分散アーキテクチャが構想されている。急成長するAI推論市場でNvidiaへの対抗軸を増やす動きであると同時に、カナダの人材と技術エコシステムへのAMDのコミットメントを示す取引でもあるとされている。
