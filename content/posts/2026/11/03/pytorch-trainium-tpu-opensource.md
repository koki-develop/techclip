---
date: "2026-11-03T08:07:27+09:00"
title: "AWSとGoogle Cloud、PyTorchをNVIDIA GPU以外で動かすバックエンドを相次ぎ公開"
description: "AWSがTrainium向け「TorchNeuron」を、Google CloudがTPU向け「TorchTPU」をそれぞれオープンソースで公開し、PyTorchのNVIDIA依存脱却に向けた動きが加速している。"
tags:
  - Cloud
  - Programming Languages
  - AI
references:
  - "https://www.publickey1.jp/blog/26/awsgoogle_cloudpytorchaws_trainiumgoogle_cloud_tpunvidia.html"
  - "https://thenewstack.io/pytorch-tpu-trainium-migration/"
---

## 概要

AWSとGoogle Cloudは、10月20〜21日に米カリフォルニア州で開催された「PyTorch Conference 2026」において、自社AIチップ向けのネイティブPyTorchバックエンドを相次いでオープンソース公開した。AWSはTrainium向けの「TorchNeuron」をパブリックベータとして、Google CloudはTPU向けの「TorchTPU」を、Metaとの共同開発により正式に発表した。両社とも、既存のPyTorchコードを大きく書き換えることなくNVIDIA製GPU以外のチップ上で実行できるようにすることを狙っており、長年PyTorchの事実上の標準環境として定着してきたNVIDIA CUDAへの依存を減らす業界的な潮流の一環と位置づけられている。

## TorchNeuronとTorchTPUの技術的特徴

AWSのTorchNeuronは、開発者がコード中のデバイス指定を`.to('neuron')`に切り替えるだけで有効化でき、eager executionやtorch.compile、標準的なPyTorch APIとの完全な互換性を維持するとされる。さらにNeuron Kernel Interface(NKI)との統合により、カスタムオペレーターの利用や性能最適化も可能になっている。一方、Google CloudのTorchTPUは、シームレスなTPUへの移行を掲げ、eager executionの最適化やtorch.compileとの統合、ハードウェアネイティブなアクセラレーションを通じて、推論・学習の両面で競争力のある性能を提供するとしている。いずれも、移行のハードルを下げる一方で、ピーク性能を引き出すには依然としてハードウェア固有の最適化が必要とされる点は共通している。

## 背景にあるNVIDIA依存からの転換

PyTorchはAI関連の研究開発において圧倒的な存在感を持つフレームワークであり、Linux Foundationの2024年の調査では、AI関連の研究開発の70%以上で利用されていると報告されている。しかし、そのソフトウェアスタックは長らくNVIDIAのCUDA環境を中心に最適化されてきたため、NVIDIA以外のアクセラレーターを選ぶハードルは高かった。AWSとGoogle Cloudによる今回の取り組みは、この構造に一石を投じるものであり、独自AIチップへの投資を加速させる両社にとって、自社ハードウェアの採用を広げる上での重要な一歩となる。

## 今後の見通し

今回の公開により、開発者はNVIDIA GPU以外の選択肢をこれまでより容易に検討できるようになる。ただし、実際の採用が進むかどうかは、互換性や性能だけでなく、コストや運用面を含めた複合的な要因に左右される。今後は対応モデルの範囲がどこまで広がるか、そして実際のワークロードでどの程度の性能を発揮できるかが注目される。
