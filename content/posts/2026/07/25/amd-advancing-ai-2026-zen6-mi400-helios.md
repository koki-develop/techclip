---
date: "2026-07-25T02:34:47+09:00"
title: "AMD、Zen 6ベースEPYC 9006とInstinct MI455X、ラックスケールHeliosを発表しAIインフラでNVIDIAに挑む"
description: "AMDが年次イベント「Advancing AI 2026」で、Zen 6アーキテクチャのEPYC 9006シリーズCPU、CDNA 5採用のInstinct MI455X GPU、ラックスケールAIシステム「Helios」を発表した。"
tags:
  - AI
  - Cloud
  - Other
references:
  - "https://www.techtimes.com/articles/321257/20260722/amd-advancing-ai-2026-opens-zen-6-venice-helios-open-ai-rack-bet.htm"
  - "https://hothardware.com/news/amd-advancing-ai-2026-epyc-9006-instinct-mi400x-helios"
---

## 概要

AMDはサンフランシスコで開催した年次イベント「Advancing AI 2026」で、TSMCの最新プロセスを採用した新型サーバーCPU「EPYC 9006」シリーズ、CDNA 5アーキテクチャ採用のAI向けGPU「Instinct MI455X」、そしてこれらを統合したラックスケールAIシステム「Helios」を相次いで発表した。データセンター向けAIインフラ市場でNVIDIAが圧倒的なシェアを握るなか、AMDはCPU・GPU・システム全体を垂直統合した製品ラインナップで本格的な対抗姿勢を打ち出した形だ。

## EPYC 9006シリーズCPUの詳細

EPYC 9006シリーズは複数のバリエーションで構成されるサーバープロセッサーファミリーで、物理コア数は8から256コアまで幅広くカバーする。フラッグシップの「EPYC 9006 SP7」は最大256コア・最高5GHz動作、TDPは最大600Wに達し、16チャネルのDDR5(最大8GT/秒)またはMRDIMM(最大12.8GT/秒)、128レーンのPCI Express Gen 6に対応する。エッジコンピューティング向けの「SP8」(8~128コア構成)、3D V-Cacheを搭載しHPC用途に特化した「9006X SP7」(最高5.15GHz、L3キャッシュ最大1152MB)、AI専用で24チャネルのLPDDR5Xメモリを採用する「9006 LP」など、用途別に細分化されたラインナップとなっている。AMDは前世代比で最大70%の性能向上、エージェントAI向けワークロードではIntel Xeon比最大245%の性能を主張している。

## Instinct MI455XとHeliosラックシステム

新型AI GPU「Instinct MI455X」はCDNA 5アーキテクチャを採用し、メモリ容量を前世代MI355Xの288GBから432GBのHBM4へと大幅に拡大した。メモリインターフェースは50%広がり、総メモリ帯域幅は23.3TB/秒に達する。演算性能はMXFP8で20ペタフロップス以上、MXFP4では40ペタフロップス以上を実現し、内部アーキテクチャもWave64からネイティブWave32設計へ刷新することで命令レイテンシの削減と分岐ペナルティの低減を図った。L2キャッシュは96MBに拡張され、スカラレジスタも倍増するなど、AI推論タスクに最適化された設計となっている。

これらのCPU・GPUを統合するラックスケールシステムが「Helios」だ。44Uのダブルワイド筐体に18個の計算トレイと6個のスイッチトレイを収容し、各計算トレイにはMI455Xを4基とVenice(Zen 6)CPUを搭載する。ラック全体では72基のGPUが単一システムとして協調動作し、GPU間帯域幅は260TB/秒、他サーバーとの接続帯域幅は43TB/秒、総HBM4メモリ容量は31TBに達する。AI演算能力はラック全体で2.9EFLOPSに及ぶ。GPU間の相互接続にはEthernet経由の「UALoE」(Ultra Accelerator Link over Ethernet)を採用し、3.6TB/秒の双方向通信を可能にしている。

## 今後の展望

今回の発表は、AMDがCPU単体の性能競争にとどまらず、GPU・相互接続・ラック筐体までを一体で設計する「システムファースト」の戦略へと舵を切ったことを示している。エッジからハイパースケールのデータセンターまで幅広い導入シナリオに対応する製品階層を整備し、急速に拡大するエージェントAIワークロードの需要を取り込む狙いだ。NVIDIAが独占的な地位を築いてきたAIインフラ市場において、垂直統合されたHeliosのようなラックスケールソリューションが実際の採用にどこまで食い込めるか、今後の市場動向が注目される。
