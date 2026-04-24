---
date: "2026-04-25T02:24:47+09:00"
title: "Google Cloud Next 2026：第8世代TPUとAIエージェント基盤で示すクラウドAI戦略"
description: "GoogleはCloud Next 2026でNvidia対抗の第8世代TPU 2バリアントとGemini Enterprise Agent Platformを発表し、企業向けAIインフラの全面強化を打ち出した。"
tags:
  - Cloud
  - AI
references:
  - "https://blog.google/innovation-and-ai/infrastructure-and-cloud/google-cloud/cloud-next-2026-sundar-pichai/"
  - "https://techcrunch.com/2026/04/22/google-cloud-next-new-tpu-ai-chips-compete-with-nvidia/"
  - "https://www.techradar.com/pro/live/google-cloud-next-2026"
---

## 概要

Googleは2026年4月22日、年次カンファレンス「Google Cloud Next 2026」でSundar Pichaiが多数の主要発表を行い、クラウドAIインフラの大規模強化を宣言した。目玉は第8世代TPUの2バリアントとなる「TPU 8t」（学習特化）および「TPU 8i」（推論特化）の投入であり、前世代比最大3倍の処理性能と80%のコストパフォーマンス向上を謳う。また、AIスーパーコンピュータ向けの新データセンターファブリック「Virgo Network」、AppleとのクラウドAI提携、Gemini Enterprise Agent Platformによるエンタープライズ向けエージェント基盤の統合強化も発表され、クラウドインフラにおけるAI競争が新たな局面を迎えた。

## 第8世代TPUの詳細

TPU 8tは学習ワークロードに最適化されており、最大9,600ユニットをクラスタリングして前世代比3倍の処理速度を実現する。TPU 8iは推論向けで、1,152ユニット接続に対応し、オンチップSRAMを3倍に拡大することでレイテンシーを大幅に低減している。さらにTPU 8tは新データセンターファブリック「Virgo Network」およびPathways/JAXソフトウェアとの組み合わせで、単一クラスターあたり100万TPU超への準線形スケーリングを実現し、従来のハイパースケール制約を突破する設計となっている。

注目すべきはGoogleのNvidiaに対するポジショニングだ。TPUはNvidiaを完全に代替するのではなく補完する位置付けとして、2026年後半にはNvidiaの最新チップ「Vera Rubin」もGoogle Cloudで提供予定であることを明らかにした。Googleが2023年にオープンソース化したネットワーキングシステム「Falcon」の改善でも協業するなど、競争と協調を並走させる戦略を採っている。

## AIエージェントとプラットフォームの強化

エンタープライズ向けAIエージェント基盤として「Gemini Enterprise Agent Platform」が発表された。数千単位のAIエージェントを構築・スケール・ガバナンス・最適化するための統合ツール群を提供し、組織規模のエージェント運用を可能にする。同プラットフォームには新モデルとしてGemini 3.1 Pro、Gemini 3.1 Flash Image、動画生成モデルVeo 3.1 Lite、音楽生成モデルLyria 3 Proも加わった。ファーストパーティモデルのAPIスループットは毎分160億トークン超に達し、前四半期比6割増という急成長が続いている。Gemini Enterpriseの有料月間アクティブユーザーも前四半期比40%増を記録した。

データ基盤・セキュリティ面では、Knowledge Catalog、Cross-Cloud Lakehouse、Deep Research Agentを新たに発表。320億ドルで買収したWizとの連携によるAIサイバーセキュリティ自動化も強化され、セキュリティエージェントは脅威の軽減時間を90%以上短縮できるとしている。Workspace Intelligenceの一般提供も開始され、M365からの移行が5倍高速化されるとの試算も示された。なお、Google社内では新規コードの75%がAI生成となっており、半年前の50%から急増するなど、自社でのAI活用も加速している。

## 市場への影響と展望

今回の発表はNvidiaが約5兆ドルの時価総額を誇るAIチップ市場において、GoogleをはじめAmazon、Microsoftなどハイパースケーラーが独自チップで存在感を高めようとする動きの一環だ。しかし各社とも短期的にはNvidiaへの依存を維持しながら、長期的な依存度低減を模索するという慎重な姿勢を取っている。AppleとのクラウドAI提携やVirgo Networkによる次世代データセンター構想はGoogleのインフラ優位性をさらに際立たせるものであり、企業ユーザーへのAIフルスタック提供という戦略の加速が鮮明になった。
