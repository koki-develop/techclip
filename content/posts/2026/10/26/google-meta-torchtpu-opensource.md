---
date: "2026-10-26T08:10:28+09:00"
title: "GoogleとMeta、PyTorchネイティブのTPUバックエンド「TorchTPU」をオープンソース化"
description: "GoogleとMetaがPyTorch Conference 2026でTorchTPUを正式オープンソース化し、1行の変更でモデルをTPUに移行できるようにした。"
tags:
  - OSS
  - AI
references:
  - "https://www.infoq.com/news/2026/10/google-meta-torchtpu/"
---

## 概要

GoogleとMetaは、米サンノゼで開催されたPyTorch Conference North America 2026において、TPU(Tensor Processing Unit)向けのネイティブPyTorchバックエンド「TorchTPU」を正式にオープンソース化したと発表した。これまでTPU上でPyTorchモデルを動かすには2020年登場のPyTorch/XLAを利用する必要があり、ソースコードへの侵襲的な変更が求められていた。TorchTPUはこの障壁を取り払うもので、Google Cloudは「TPUはGPU、CPUと並ぶPyTorchのネイティブな選択肢に加わった」と述べている。

## 技術的な詳細

TorchTPUの最大の特徴は、既存のPyTorchモデルを`model.to("cuda")`から`model.to("tpu")`へと1行書き換えるだけでTPU上に移行できる点にある。バックエンドはPyTorchの低レベルディスパッチャに直接組み込まれており、Hugging Face製モデルやvLLM、SGLang、TorchTitanといった既存のエコシステムともそのまま互換性を持つ。今回のオープンソース化では、TorchTPU本体に加えてvLLM-TorchTPU、SGLang-TorchTPU、TorchTitanの合計4つのリポジトリが公開された。あわせて、オンボーディングや診断、パフォーマンスチューニングを自動化する「TPUエージェントスイート」もプレビュー版として発表されている。

性能面では、Googleが8,000基を超えるTPUチップ上でほぼ線形なスケーリングと、チップ当たり一貫したスループットを実証したという。具体的には、Qwen3の235Bパラメータ規模のMixture-of-Expertsモデルを8,192基のTPU v7xチップ上で動作させ、モデルFLOPs利用率(MFU)28%を達成した。ただし記事では、1行の変更だけでは最適な性能が出るとは限らないとも指摘されている。モデルの形状、シャーディング戦略、演算がGPUアーキテクチャに最適化された状態のままになっている場合があり、TPU向けに最大限の性能を引き出すには追加のチューニングが必要になるという。

## 協業の背景と今後の展望

Metaにとっての狙いはハードウェアの多様化にある。記事中でMetaは「単一のハードウェアアーキテクチャに縛られるわけにはいかない」との立場を示し、両社はTorchTPUを通じてTPUを「PyTorchのファーストクラスなネイティブターゲット」として確立することを共同で目指している。

なお、同時期にAWSもTrainium向けのネイティブPyTorchバックエンド「TorchNeuron」を発表しており、PyTorchのカスタムハードウェア向け拡張ポイントであるPrivateUse1を通じて登録される仕組みを採用している。GPU以外のアクセラレータをめぐるこうした動きが相次いだことは、PyTorchエコシステムが特定のハードウェアベンダーへの依存から脱却し、複数のアクセラレータを同列に扱う方向へ進んでいることを示している。
