---
date: "2026-09-24T08:09:47+09:00"
title: "クアルコム、フラッグシップSoCを初の2階層化 「Snapdragon 8 Elite Gen 6」と最上位「Extreme Gen 6」を発表"
description: "クアルコムがTSMC 2nmプロセス採用の新フラッグシップSoC2製品を発表し、最上位Extreme Gen 6は世界初の5GHz動作CPUと300億パラメータ級AIモデルのオンデバイス実行を実現した。"
tags:
  - Other
references:
  - "https://www.techtimes.com/articles/327920/20260923/qualcomm-snapdragon-summit-debuts-dual-2nm-chips-extreme-gen-6-runs-30b-ai-models-offline.htm"
  - "https://www.androidheadlines.com/2026/09/qualcomm-just-announced-the-snapdragon-8-elite-gen-6-and-extreme-gen-6-its-fastest-chips-yet.html"
  - "https://www.gizmochina.com/2026/09/23/qualcomm-debuts-snapdragon-8-elite-extreme-gen-6-and-8-elite-gen-6-as-worlds-first-mobile-processors-with-5ghz-cpu/"
---

## 概要

クアルコムはSnapdragon Summitで、TSMCの2nm（N2P）プロセスを採用した新フラッグシップSoC「Snapdragon 8 Elite Gen 6」と、その上位モデルとなる「Snapdragon 8 Elite Extreme Gen 6」を発表した。同社が9年間続けてきた「1世代1チップ」のフラッグシップ体制を転換し、標準・上位の2階層構成を初めて導入するもので、業界では異例の戦略転換と受け止められている。両モデルとも独自CPUアーキテクチャ「Oryon」をベースに、2基のプライムコア（最大5.0GHz）と6基のパフォーマンスコア（最大4.0GHz）を搭載し、世界初となる5GHz駆動のモバイル向けCPUを実現した。CPU性能はGen 5比で標準のGen 6が約10%、Extreme Gen 6が約13%向上している。

## Extreme Gen 6が実現するオンデバイスAI

最上位モデルのExtreme Gen 6を特徴づけるのが、新設計の「Flex Cache」アーキテクチャだ。単一スレッドのワークロードがキャッシュプールのほぼ全体にアクセスできる仕組みで、共有メモリ容量も標準モデル比で50%増加している。この拡張メモリと、AI対応のMatrix Coresを備えたGPU「Adreno 850」（18MBキャッシュ、前世代（Gen 5）比44%のパフォーマンス向上）の組み合わせにより、これまでクラウド接続が前提だった300億パラメータ級の混合専門家（MoE）モデルを、サーバーに接続せずスマートフォン単体でオフライン実行できるようになった。標準のGen 6はAdreno 845（12MBキャッシュ）を搭載し性能向上幅は35%にとどまるが、NPU性能はGen 5比14%向上し、いずれのモデルもHexagon AIエンジンに新たな「Element Accelerator」を追加している。センシング機能では、デュアルマイクロNPUを備えたSensing Hubが最大85%の性能向上と20%の効率改善を果たした。このほかExtreme Gen 6は次世代のLPDDR6メモリに初めて対応し、ビデオ撮影は8K/60fps・4K/240fpsのスローモーションに対応する（標準モデルは8K/30fps・4K/120fps）。接続面では両モデル共通でX105 5Gモデム（下り14.8Gbps、上り4.2Gbps）とWi-Fi 8対応のFastConnect 8800を搭載する。

## 2階層化の背景とコストへの影響

クアルコムが今回あえて2つのフラッグシップを用意した狙いは、DRAM価格の高騰への対応にあるとみられる。OEM各社が価格帯に応じてチップを選び分けられるようにすることで、部材コスト上昇の影響を製品ラインナップ全体で吸収しやすくする狙いだ。もっとも、採用するTSMCのN2Pプロセスはウェハー単価が約3万ドルと3nm世代比で5割高く、Extreme Gen 6は1チップあたり300ドルを超える見通しで、2027年にかけて一部端末の店頭価格を押し上げる要因になるとの指摘もある。なお、Adreno 850のGPU性能が前世代比44%向上したとしても、その恩恵が実感できるのはAdreno Neural Fusion対応のゲームやカメラ処理といった負荷の高い用途が中心で、日常的なアプリ利用での体感差は初年度限定的とみられる。

## 競合状況と採用端末

製造プロセスの面では、AppleのA20 Pro（TSMC N2ベース）やMediaTekのDimensity 9600 Pro（N2P採用）も同じ2nm世代に到達しており、モバイルSoC各社が足並みを揃える形となった。一方でXiaomiは自社開発のTSMC 3nm製チップ「Xring O3」を並行投入する計画で、大手OEMの一部にクアルコム依存を下げる動きがあることもうかがえる。搭載端末としては、Motorola「Signature 27」（Extreme搭載、2026年末発売予定）、Xiaomi「18 Pro」（標準搭載）・「18 Pro Max」（Extreme搭載、2026年第4四半期に中国展開）、HONOR「Magic9 Pro Max」（9月28日発表予定、Extreme搭載）のほか、OnePlus「16」やiQOO「16」への採用も見込まれている。
