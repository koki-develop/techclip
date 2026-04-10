---
date: "2026-04-11T02:24:14+09:00"
title: "Intel OpenVINO 2026.1リリース、llama.cppバックエンドのプレビュー対応とQwen3 VL・GPT-OSS 120Bをサポート"
description: "IntelがOpenVINO 2026.1をリリースし、llama.cppのOpenVINOバックエンドをプレビュー機能として追加、Intel CPU・GPU・NPU上でのGGUFモデル推論を最適化できるようになった。"
tags:
  - AI
  - OSS
references:
  - "https://www.phoronix.com/news/OpenVINO-2026.1-Released"
  - "https://github.com/openvinotoolkit/openvino/releases/tag/2026.1.0"
---

## 概要

IntelはオープンソースのAI推論フレームワーク「OpenVINO」のバージョン2026.1を正式リリースした。今リリースの最大の目玉は、llama.cppのOpenVINOバックエンドのプレビュー追加だ。これにより、llama.cppユーザーがIntel CPU・GPU・NPU上でGGUF形式のモデルを最適化した形で実行できるようになる。検証済みのGGUFモデルには、Llama-3.2-1B-Instruct-GGUF、Phi-3-mini-4k-instruct-gguf、Qwen2.5-1.5B-Instruct-GGUF、Mistral-7B-Instruct-v0.3が含まれる。

新たなモデルサポートとして、CPU・GPU両方でQwen3 VL（ビジョン言語モデル）への対応が追加された。また、GPT-OSS 120BのCPU推論サポートも導入され、Qwen3-VL、Qwen2.5-VL、LLaVa-NeXT-Videoを統合的に切り替えられるVLMチャットボット用ノートブックも提供されている。

## 技術的な詳細

ハードウェアサポートの面では、Intel Core Series 3プロセッサーおよびArc Pro B70グラフィックス（32GBメモリ搭載）への対応が追加された。これにより、シングルGPUで20〜30Bパラメーター規模のLLMを推論できるようになる。

パフォーマンス最適化として、Prompt Lookup DecodingがビジョンLMパイプラインにも拡張された。また、LTX-Videoの動画生成においてRMSNormとRoPEオペレーターの融合によるエンドツーエンドの高速化が実現されている。さらに、TaylorSeer Liteキャッシュ機構がFlux、SD3、LTX-Videoといった拡散トランスフォーマー推論パイプラインを加速する。

## 非推奨・廃止事項

今リリースでは、非推奨だった`openvino.runtime`名前空間が正式に削除された。また、CPUの最小要件がAVX2命令セットへと引き上げられ、SSE命令セットのサポートが廃止された。古いハードウェアを利用しているユーザーは移行の要否を確認する必要がある。
