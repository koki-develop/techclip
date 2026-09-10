---
date: "2026-09-10T18:14:11+09:00"
title: "Google DeepMind、ヒトゲノムの全90億通りの一塩基変異を予測する「AlphaGenome Atlas」を公開"
description: "Google DeepMindがAIモデルAlphaGenomeを用い、ヒトゲノムで起こりうる全90億通りの一塩基変異の生物学的影響を予測したデータベース「AlphaGenome Atlas」を無料公開した。"
tags:
  - AI
references:
  - "https://deepmind.google/blog/alphagenome-atlas-a-predictive-map-of-every-possible-dna-letter-change-in-the-human-genome/"
---

## 概要

Google DeepMindは9月8日、ヒトゲノムで理論上起こりうる一塩基変異(SNV)90億通りすべてについて、その分子的影響をあらかじめ予測したデータベース「AlphaGenome Atlas」を公開した。予測にはDeepMindが開発したAIモデル「AlphaGenome」を用いており、RNAスプライシング、遺伝子発現、クロマチンアクセシビリティなど数千種類の分子的効果を網羅する。さらにミスセンス変異予測モデル「AlphaMissense」と統合した単一指標「AVI(AlphaGenome Variant Impact)スコア」により、個々の変異の影響度を一つの数値で把握できるようにした点が特徴だ。これまで実験的に検証することが事実上不可能だった規模のゲノム変異を、計算科学によって網羅的にマッピングした試みといえる。

## 開発の背景と技術的アプローチ

ヒトゲノム上で起こりうる一塩基変異は90億通りにのぼり、これを実験室ですべて検証することは不可能とされてきた。DeepMindは、2億件以上のタンパク質立体構造を予測し研究コミュニティに広く活用されている「AlphaFold」データベースの成功戦略を踏襲し、AlphaGenomeによる大規模予測を無料の研究基盤として公開することで、ゲノム機能解析を民主化する狙いがあるとしている。公開形態は、学術研究向けの無料ウェブポータルに加えてAlphaGenome API、Google Antigravity上でのスキル提供という複数の経路が用意されており、Google Cloudを通じた商用利用も近く開始される予定だ。

## 実証研究と専門家の評価

DeepMindはAtlasの有用性を複数の実証研究で示している。希少疾患研究に取り組むGREGoR Consortiumとの協力では、てんかん脳症に関連するDNM1遺伝子の変異を特定・検証した。また英国バイオバンクの約54,000人分のデータを用いた形質解析では、非コード領域の変異による遺伝子との関連を従来より22%多く検出できたという。Broad InstituteのAnne O'Donnell-Luria氏とLaura Covill氏の研究では、AVIスコアを用いて変異を絞り込んだ結果、AlphaGenomeの予測が変異の機能様式を具体的に示したことが示され、University of ExeterのGareth Hawkes氏は統計的ノイズの低減効果を実証したとしている。

## 今後の展望と課題

DeepMindのチームはAlphaGenome Atlasについて「終着点ではなく出発点(a baseline rather than an endpoint)」と位置づけており、モデルの改良に伴って予測精度は今後さらに向上する見込みだとしている。一方で、現時点では医療診断への使用は承認されておらず、あくまで研究用途のツールという位置づけである点には注意が必要だ。疾患関連変異の絞り込みや創薬標的の探索において研究者の効率を大きく高める可能性がある一方、臨床応用に向けては規制上の検証プロセスを経る必要があり、今後の実用化の進展が注目される。
