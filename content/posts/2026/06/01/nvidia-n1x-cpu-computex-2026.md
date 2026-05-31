---
date: "2026-06-01T02:28:22+09:00"
title: "NVIDIAがCOMPUTEX 2026でARMベースSoC「N1X」を発表——約10年ぶりのコンシューマー向けCPU参入"
description: "NVIDIAがCOMPUTEX 2026のGTC Taipeiキーノートで、ARMベース20コアCPUとRTX 5070相当のGPUを統合したWindows PC向けSoC「N1X」を正式発表した。"
tags:
  - Other
references:
  - "https://www.ghacks.net/2026/05/31/nvidia-set-to-reveal-first-consumer-cpu-in-over-a-decade-at-computex-2026/"
  - "https://www.techtimes.com/articles/317446/20260530/computex-2026-jensen-huang-keynote-n1x-reveal-arc-g3-snapdragon-c-all-land-this-week.htm"
  - "https://www.nvidia.com/en-tw/gtc/taipei/computex/"
---

## 概要

NVIDIAのCEOジェンスン・フアン氏は2026年6月1日、台湾・台北で開催されたCOMPUTEX 2026のGTC Taipeiキーノートにおいて、コンシューマー向けSoC「N1X」を正式に発表した。これはTegra X1以来、実に約10年ぶりとなるNVIDIAのコンシューマー向けCPU参入であり、Windows on Arm市場への本格展開を宣言するものだ。発表に先立ち、NVIDIAはMicrosoftおよびArmと協調して「A new era of PC」というフレーズを用いたティーザーキャンペーンを展開し、COMPUTEX 2026の座標をヒントとして公開するなど、大きな注目を集めていた。

## 技術仕様

N1XはARMアーキテクチャに基づくSoCで、MediaTek設計の20コアCPU（10コア×2クラスター構成）とBlackwellアーキテクチャベースのiGPUを一体化している。GPUはCUDAコア6,144基を搭載し、ディスクリートGPUのGeForce RTX 5070に相当するコア数を誇る。製造プロセスはTSMC 3nmを採用し、NVLinkで最大300GB/秒の帯域幅でCPU・GPU間を接続する。RAMは最大128GBを8,533 MT/sで利用可能で、完全なCUDAソフトウェアスタックをサポートする点がQualcomm Snapdragon XやApple Mシリーズとの大きな差別化要素となっている。デスクトップ向けと比較してクロック周波数と消費電力を抑えたノートPC・2-in-1向けの設計となっている。

## 市場への影響と競合環境

N1XはNVIDIAが開発者・研究者向けに展開した「Project Digits」のコンシューマー版と位置づけられており、WindowsネイティブアプリのArm対応加速と、Arm PCの価格帯改善を狙う。これまでApple M系チップがArmプラットフォームのパフォーマンスで圧倒的な存在感を示してきた中、NVIDIAのGPUコンピューティング資産とCUDAエコシステムを組み合わせたN1Xは、Qualcomm Snapdragon Xシリーズに次ぐ有力な対抗軸として業界から注目されている。N1X搭載デバイスはDell・Lenovo・ASUS・MSIが2026年末までにラップトップおよび2-in-1ノートPC向けに製品化する予定で、2027年初頭には次世代「N2」シリーズへの移行も見込まれている。