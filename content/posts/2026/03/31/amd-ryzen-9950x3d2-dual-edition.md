---
date: "2026-03-31"
title: "AMD、両チップレットに3D V-Cache搭載の「Ryzen 9 9950X3D2 Dual Edition」を正式発表——208MBキャッシュで4月22日発売"
description: "AMDはデスクトップPC向け初の両チップレット3D V-Cache搭載CPU「Ryzen 9 9950X3D2 Dual Edition」を正式発表し、208MBキャッシュと200W TDPで2026年4月22日に発売する。"
tags:
  - Other
references:
  - "https://www.theregister.com/2026/03/26/amd_crams_208mb_of_cache/"
  - "https://www.tweaktown.com/news/110688/amd-officially-unveils-the-ryzen-9-9950x3d2-dual-edition-armed-with-208mb-of-cache-and-a-200w-tdp/index.html"
  - "https://www.tomshardware.com/pc-components/cpus/amd-makes-the-flagship-ryzen-9-9950x3d2-official-first-dual-cache-x3d-cpu-arrives-in-april-with-208mb-cache-200w-tdp-promising-modest-performance-gains"
---

## 概要

AMDは2026年3月26日、デスクトップPC向け初の両チップレット3D V-Cache搭載プロセッサ「Ryzen 9 9950X3D2 Dual Edition」を正式に発表した。4月22日に発売予定で、16コア/32スレッド構成に208MB（L2: 16MB + L3: 192MB）の大容量キャッシュを搭載し、AIや創作ワークロードを主なターゲットとするフラッグシップ製品として位置付けられている。

前世代の「Ryzen 9 9950X3D」は片方のチップレットのみに64MBの3D V-Cacheスタックを積んでいたが、9950X3D2では両方のコンピュートダイそれぞれに64MBのSRAMタイルを搭載することで、合計L3キャッシュを128MBから192MBへと拡張。これがシリーズ名末尾の「2」が示す最大の革新点となっている。

## 技術的な詳細

主なスペックは以下のとおりだ。ベースクロックは4.3 GHz、ブーストクロックは5.6 GHz、TDPは200Wとなっている。ブーストクロックは前世代の9950X3D（5.7 GHz）より100 MHz低下しているが、これは両ダイにキャッシュを積んだことによる発熱増大への対処とみられる。

両チップレットにV-Cacheを搭載した設計はパフォーマンス面で一定の恩恵をもたらすが、同時にダイをまたぐ通信（クロスダイ通信）によるレイテンシ増加というトレードオフも生じる。このためゲーミング性能への悪影響を抑えるにはコアパーキング（一部コアを休止させる技術）が依然として必要とされる。The Registerによれば、9950X3Dと比較したプロダクションワークロードでの性能向上は5〜13%程度と報告されており、レンダリング・コンパイル・AI・データサイエンスといった用途で恩恵が見込まれる。

## 位置付けと展望

AMDは本製品をゲーマー向けではなく、AIワークロードや映像制作・3Dレンダリングといったクリエイター向けの最上位CPUとして訴求している。Tom's Hardwareは「控えめな性能向上（modest performance gains）」という表現を使っており、5〜13%という数字はハイエンドCPUの世代間差異としては大きくないとも受け取れる。価格は未発表だが、現行の9950X3Dが649ドル以上で販売されていることを踏まえると、さらに上の価格帯になることが予想される。4月22日の発売後、実際のベンチマーク結果に注目が集まりそうだ。
