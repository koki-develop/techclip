---
date: "2026-08-02T14:58:48+09:00"
title: "NOAA、気象予測の自前スーパーコンピュータを全廃しGoogle Cloudへ全面移行"
description: "米海洋大気庁(NOAA)が2027年12月までに気象予測業務を自前のHPE Cray製スーパーコンピュータからGoogle Cloudへ全面移行し、商用クラウドで運用する初の国家気象予測センターとなる。"
tags:
  - Cloud
  - AI
references:
  - "https://www.theregister.com/hpc/2026/07/29/noaa-ditches-weather-predicting-supercomputers-for-google-cloud/5280697"
  - "https://www.hpcwire.com/off-the-wire/noaa-shifts-weather-forecast-supercomputing-operations-to-the-cloud/"
  - "https://www.noaa.gov/news-release/noaas-use-of-cloud-infrastructure-grows-to-include-weather-prediction-models"
---

## 概要

米海洋大気庁(NOAA)は、自前のHPE Cray製スーパーコンピュータによる気象予測業務を廃止し、2027年12月までにGoogle Cloudへ全面移行すると発表した。これにより同庁は、商用クラウド基盤上で完全に運用される初の国家気象予測センターとなる。移行対象は「Weather and Climate Operational Supercomputing System」で、現在General Dynamicsが管理するDogwoodおよびCactusという2台のHPE Cray製スーパーコンピュータ(合計で約14ペタフロップスの演算能力)が置き換えられる。NOAAは「クラウドベースの高性能計算(HPC)により、オンプレミスシステムが抱えていた従来のボトルネックを解消し、研究成果を実運用へ移すプロセスを加速できる」と説明しており、台風シーズンなど悪天候が集中する時期に計算資源を柔軟に増強し、平常時には縮小するといった弾力的な運用を目指す狙いがある。

## 技術的な詳細

Googleは、AMD EPYCプロセッサをベースとした新しい仮想マシン「H4D」をNOAA向けに展開する計画だ。H4DはハイパーバイザーによってGoogleのネットワーキングおよびオーケストレーション技術と統合されており、仮想化環境でありながらスーパーコンピュータ級の並列処理性能を実現するとしている。運用面では、クラスタ展開用の「Cluster Toolkit」、保守管理用の「Cluster Director」、ジョブスケジューリング用の「Batch」といったGoogle Cloudのツール群が活用される見込みだ。料金体系については、長期契約なしでコア時間あたり最低3セントからという価格設定が示されている。またAIの活用面では、NOAAはGoogle DeepMindの技術へのアクセスも得ることになり、AIを用いたグローバル予報システム(AI Global Forecast System)の開発に役立てる方針だ。

## 背景と今後の見通し

政府機関が気象予測という国家の安全保障やインフラに直結する重要業務をクラウドへ全面移行する動きは、世界的に見ても先駆的な事例となる。同様の流れとして、英国気象庁(Met Office)もMicrosoft Azureへの移行を進めており、各国の気象機関が自前のスーパーコンピュータ運用から商用クラウドへとシフトする傾向がうかがえる。NOAAにとっては、老朽化しがちなオンプレミス設備の維持コストや調達サイクルの制約から脱却し、需要に応じた俊敏なスケーリングとAI技術への迅速なアクセスを両立させることが狙いとみられる。2027年12月の完全移行に向けて、今後は既存モデルのクラウド環境への移植や、DeepMindの技術を組み込んだ次世代予報システムの開発状況が注目される。
