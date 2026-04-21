---
date: "2026-04-21T10:38:25+09:00"
title: "SK hynix、NVIDIA Vera Rubin向け192GB SOCAMM2メモリを量産開始――RDIMM比2倍の帯域幅と75%超の電力効率を実現"
description: "SK hynixが1cnmプロセス・LPDDR5X採用の192GB SOCAMM2メモリモジュールの量産を開始し、NVIDIAの次世代AIプラットフォーム「Vera Rubin」向けに出荷を始めた。"
tags:
  - Other
  - AI
references:
  - "https://news.skhynix.com/mass-production-socamm2-192gb/"
  - "https://www.prnewswire.com/news-releases/sk-hynix-begins-mass-production-of-192gb-socamm2--setting-a-new-standard-for-ai-server-memory-performance-302746711.html"
  - "https://wccftech.com/sk-hynix-mass-produces-192-gb-socamm2-memory-for-nvidia-vera-rubi-ai-datacenters/"
---

## 概要

SK hynixは2026年4月19日、第6世代10nmクラス（1cnm）プロセスとLPDDR5X低消費電力DRAMを採用した192GB SOCAMM2メモリモジュールの量産開始を正式発表した。SOCAMM2（Small Outline Compression Attached Memory Module 2）は、これまでスマートフォンなどモバイル向けに用いられてきたLPDDR系メモリをサーバー環境に適用した次世代規格であり、従来のRDIMM（Registered Dual In-Line Memory Module）と比較して帯域幅は2倍以上、電力効率は75%超の改善を実現する。データ転送速度は前世代SOCAMM1の8.5 Gbpsから9.6 Gbpsへ向上している。SK hynixのCMO兼AI Infraヘッドを務めるJustin Kim社長は「192GB SOCAMM2の供給により、SK hynixはAIメモリ性能の新標準を確立した」とコメントした。

## 技術的な詳細

SOCAMM2はLPDDRチップを垂直方向にスタックすることで高い面積効率と電力効率を両立しており、従来の標準DDR5よりも多いI/Oピン数を持つ。コネクタには圧着式を採用し、信号品質（SI）の向上とモジュール交換の容易さを確保している。HBM4やDDR5 RDIMM、CXL拡張メモリと並ぶ多層メモリ階層の中では「中間層」に位置し、頻繁にアクセスされるホットデータのバッファリングやLLMのトレーニング・推論時のメモリボトルネック解消を担う役割が期待されている。大規模言語モデル（数千億パラメータ規模）の学習において、SOCAMM2は低消費電力で高い処理スループットを提供できるとSK hynixは説明している。

## NVIDIA Vera Rubinとの関係

本製品はNVIDIAの次世代AIデータセンタープラットフォーム「Vera Rubin」向けに設計されており、同プラットフォームは2026年後半の展開が予定されている。NVIDIAはサプライチェーン多様化の観点からSK hynix・Samsung・Micronの3社からSOCAMM2を調達する方針を採っている。Samsungは192GBの量産、Micronは2026年3月に世界初となる256GBサンプルの出荷を完了させており、各社が供給競争を展開している。SK hynixはVera Rubinの製品投入前に量産体制を早期確立することで、グローバルなクラウドサービスプロバイダー（CSP）顧客の需要を取り込む戦略を取っている。AIの活用がインファレンスから大規模トレーニングへとシフトする中、SOCAMM2はこのトレンドを支える主記憶ソリューションとして業界から注目を集めている。