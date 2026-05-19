---
date: "2026-05-20T02:49:44+09:00"
title: "BlackstoneとGoogleがTPUベースのAIインフラ合弁会社を設立——50億ドル初期投資でNVIDIA依存低減へ"
description: "BlackstoneとGoogleがTPUをコンピュート・アズ・ア・サービスとして提供する合弁会社を設立し、Blackstoneが50億ドルの初期出資（レバレッジ込み総額約250億ドル）を行うと発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://www.cnbc.com/2026/05/19/blackstone-google-ai-data-center-joint-venture-tpu.html"
  - "https://www.datacenterdynamics.com/en/news/blackstone-and-google-team-up-for-new-tpu-based-cloud-platform/"
---

## 概要

GoogleとBlackstoneは2026年5月19日、米国内でGoogleのTPU（Tensor Processing Unit）をコンピュート・アズ・ア・サービスとして提供する合弁会社の設立を共同発表した。Blackstoneが50億ドルの初期出資を行い、レバレッジを含めた総額は約250億ドルに達する見込みだ。2027年までに500MW（メガワット）のデータセンター容量を稼働させることを目標としており、急増するAI需要に対応する大規模インフラ投資として注目されている。合弁会社のCEOにはGoogle出身のBenjamin Treynor Slossが就任予定で、同氏はGoogleにおけるSRE（サイト信頼性エンジニアリング）の創設者としても知られる。

## 戦略的背景：NVIDIA依存からの脱却

今回の取り組みの核心は、データセンター向けGPUで圧倒的シェアを持つNVIDIA製品への依存を低減することにある。AI向け計算需要の急拡大とともに、NVIDIAのH100やB200といったGPUは需給が逼迫し、価格高騰が続いている。GoogleのTPUはGoogleが自社AI/MLワークロード向けに独自開発した専用アクセラレータであり、特定の推論・学習ワークロードにおいてGPUと同等以上の性能を発揮する。この合弁会社を通じてTPUを外部顧客に広く提供することで、GoogleはTPUのエコシステムを拡大しつつ、AI インフラ市場における差別化を図る。

## 資金構造とデータセンター計画

Blackstoneによる50億ドルの自己資本投資に加え、レバレッジ（借入）を組み合わせることで総投資規模は約250億ドルに達する計画だ。AI特化のデータセンターとしては異例の大規模投資であり、Blackstoneにとっても同社のデータセンター・インフラ投資戦略の延長線上に位置づけられる。2027年までに500MWの容量を稼働させる計画は、大規模言語モデルの学習・推論に必要な電力需要を見据えたもので、立地・電力調達・冷却設備の確保が今後の重要課題となる。

## 今後の展望

TPUベースのクラウドプラットフォームが大規模に展開されれば、AIインフラ市場の競争構図に変化をもたらす可能性がある。現在のAIクラウド市場はAWS、Azure、Google Cloudの三強がNVIDIA製GPUを基盤として競っているが、今回の合弁会社がTPUという代替コンピュートを大規模に提供することで、GPU中心の市場構造に楔を打ち込む形となる。一方、TPUのソフトウェアエコシステム（主にJAXやTensorFlowへの依存）はNVIDIA CUDAと比較してまだ限定的であり、顧客獲得においては技術的な移行コストが課題となる見通しだ。
