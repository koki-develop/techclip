---
date: "2026-04-20T02:17:42+09:00"
title: "DeepSeek V4、4月下旬リリースへ——1兆パラメータ・Huawei Ascend専用設計でNVIDIA不要の初フロンティアモデルへ"
description: "DeepSeekの次世代モデルV4が4月下旬にリリース予定で、1兆パラメータのMoEアーキテクチャ、100万トークンのコンテキスト長、Huawei Ascend 950PRチップ専用最適化という三つの特徴を備えている。"
tags:
  - AI
references:
  - "https://www.gizchina.com/ai/deepseek-v4-expected-to-launch-in-late-april-with-massive-parameter-scale"
  - "https://findskill.ai/blog/deepseek-v4-release-date-specs/"
  - "https://ghost.codersera.com/blog/deepseek-v4-release-date-features-benchmarks/"
  - "https://www.trendforce.com/news/2026/04/07/news-decoding-deepseek-v4-how-huaweis-ascend-950-pr-is-powering-chinas-push-to-break-cuda-dependence/"
---

## 概要

DeepSeekは次世代フラッグシップモデル「V4」を2026年4月下旬にリリースする見通しだ。2度の延期を経て最終調整が続いているとされ、ロイターも「今後数週間以内」のリリースを報道している。V4の軽量版にあたる「V4-Lite」はすでに3月9日からテスト段階に入っており、本番リリースの直前段階にあるとみられる。

最大の注目点はハードウェア戦略にある。V4はNVIDIAではなくHuaweiのAscend 950PRチップ向けに最適化された、初の「フロンティア級AIモデル」として位置づけられている。ロイターが4月3日に報じたように、Alibaba・ByteDance・Tencentといった中国大手テック企業は数十万ユニット規模でAscend 950PRを大量発注しており、中国国内のAIインフラがNVIDIA依存から脱却しつつある様子が鮮明になってきた。

## 技術的な詳細

V4はMixture-of-Experts（MoE）アーキテクチャを採用し、総パラメータ数は1兆に達する見込みだが、推論時に実際に活性化されるのは約370億パラメータにとどまる。これにより、1兆パラメータ相当の知識を保有しながら37Bモデルと同程度の計算コストで推論できる設計となっている。コンテキストウィンドウは100万トークンで、128Kトークン時点での文脈検索精度は94%（従来45%）と大幅に向上している。マルチモーダル対応（テキスト・画像・動画のネイティブ生成）も搭載予定だ。

内部アーキテクチャには三つの革新が盛り込まれている。まず、ハッシュベースのO(1)検索で静的知識を扱う「Engramコンディショナルメモリ」は、アテンション機構の二次スケーリング問題を回避する。次に、トークンの複雑度に応じて密なアテンションと疎なアテンションを動的に切り替える「DeepSeek Sparse Attention（DSA）」が推論コストを削減する。最後に、1兆パラメータモデルの安定した訓練を実現する「Manifold-Constrained Hyper-connections（mHC）」が全体の学習品質を支える。推論速度はV4-Liteの段階でV3比30%の高速化が確認されており、価格は入力約$0.30/百万トークン、出力$0.50/百万トークンと競合比1/20〜1/50程度となる見込みだ。

## 米国輸出規制とCUDA脱却の意味

V4がHuawei Ascend専用設計を採用した背景には、米国の輸出規制によりNVIDIAチップへのアクセスが制限されていることがある。TrendForceの分析によれば、HuaweiはAscend 950PRにおいて2 PFLOPS（FP4）の演算性能と2TB/sのインターコネクト帯域幅を実装し、112GBの独自HiBLメモリを搭載することで外部サプライチェーンへの依存を削減している。DeepSeekが推論・学習の両面でAscend上の完全なソフトウェアスタックを構築できれば、コア開発パイプラインはCUDAから独立できると専門家は見る。

ベンチマーク予測では、SWE-benchがV3.2の67.8%から81%程度に、HumanEvalが82%から90%程度に、MMLU-Proが85.0%から89%程度に向上するとされており、コーディング・推論能力の大幅な伸びが期待されている。NVIDIAのCEOもこの動向をAI覇権に対する重大な脅威として言及しており、V4のリリースは米中AI開発競争の新たな転換点となる可能性がある。
