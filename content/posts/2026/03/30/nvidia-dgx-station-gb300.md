---
date: "2026-03-30"
title: "Nvidia DGX Station GB300が注文受付開始、748GBメモリ・20PFLOPSのデスクトップAIスーパーコンピュータ"
description: "NvidiaがGTC 2026でGB300 Grace Blackwell Ultra搭載のDGX Stationを正式発表し、パートナー各社経由での注文受付を開始した。"
tags:
  - AI
  - Other
references:
  - "https://www.tomshardware.com/tech-industry/artificial-intelligence/nvidia-launches-dgx-station-with-its-bleeding-edge-gb300-grace-blackwell-superchip-now-available-to-order-and-will-begin-shipping-in-the-coming-months"
---

## 概要

NvidiaはGTC 2026において、GB300 Grace Blackwell Ultraデスクトップスーパーチップを搭載した新型DGX Stationを正式に発表し、注文受付を開始した。昨年のGB200 Blackwell搭載モデルに続くアップグレードモデルで、デスクトップ筐体ながらデータセンター級のAI演算性能を実現する。72コアのGrace CPUとBlackwell Ultra GPUを900GB/sのNVLink C2Cインターフェースで接続し、最大20ペタフロップスのAI演算性能を提供する。1兆パラメータ規模のモデルの開発・実行にも対応可能で、研究者やデータサイエンティスト向けのオフィス設置型AIワークステーションとして位置づけられている。

## スペックと技術的特徴

DGX Station GB300は、合計748GBのオンボードメモリを搭載する。内訳はCPU側が496GBのLPDDR5X（帯域幅396GB/s）、GPU側が252GBのHBM3eメモリ（帯域幅7.1TB/s）となっている。なお、GPU側のHBM3eメモリ容量は当初2025年に発表された仕様（288GB、帯域幅8TB/s）から減少しており、8スタック中7スタックを有効化したB300チップが使用されているとみられる。

新たにNVFP4精度フォーマットに対応し、NVFP4演算性能は前世代Blackwell比で50%向上している。NVFP4はFP8に近い精度を維持しながらメモリフットプリントをFP8比1.8倍、FP16比3.5倍削減できるため、大規模モデルの効率的な推論・学習が可能となる。ネットワーク接続にはConnectX-8 SuperNICを採用し、2つのQSFP112ポートで最大800Gb/sの通信速度をサポートする。PCIe Gen5 x16スロットやRTX PRO Blackwellグラフィックスカードのサポートも備え、2台のDGX Stationを接続してスケールアウトする構成にも対応する。システム全体のTDPは1,600Wとなっている。

## 価格と販売体制

Nvidia自体は公式価格を公表していないが、MSI XpertStation WS300がCDWで96,995.99ドルで掲載されており、市場価格は約10万〜12.5万ドルの範囲とみられる。前世代のDGX Stationが上位構成で約15万ドルだったことを考えると、性能向上に対して価格は抑えられている。今回Nvidiaはファウンダーズエディションの販売を行わず、CPU・GPU統合済みのマザーボードをパートナーに供給する方式を採用している。Asus、Dell、Gigabyte、MSI、Supermicro、HPの各社から注文が可能で、今後数ヶ月以内に出荷が開始される予定だ。
