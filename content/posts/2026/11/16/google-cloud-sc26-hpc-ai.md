---
date: "2026-11-16T18:13:03+09:00"
title: "Google Cloud、Gemini駆動のエージェント型HPCワークフローとAlphaEvolveのクラウド規模実行機能をSC26前に発表"
description: "Google CloudはSC26を前に、Cluster Toolkitを拡張したエージェント型HPCワークフローと、進化的最適化ツール「AlphaEvolve」をクラウド規模で実行する新機能を発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/topics/hpc/whats-new-in-hpc-and-ai-at-sc26"
---

## 概要

Google Cloudは11月13日、スーパーコンピューティング会議SC26（11月15日～20日、シカゴ）を前に、HPC(高性能計算)基盤をエージェントAIで強化する複数の発表を行った。中心となるのは、インフラ構築支援ツール「Cluster Toolkit」をエージェント型ワークフローへ拡張したことと、DeepMind開発のGemini駆動型進化的最適化ツール「AlphaEvolve」をCloud Batch上でクラウド規模で実行できるようにしたことだ。同社は、一般目的のAIモデルをそのまま本番HPCワークロードに使うだけでは、互換性のないストレージ層とVMの組み合わせや配置ポリシーの見落とし、マルチノードMPI障害の診断停止といった問題が起きやすいとし、HPCや科学分野の専門知識を再利用可能な「エージェントスキル」としてパッケージ化することが解決策になると位置づけている。

## Cluster Toolkitのエージェント拡張とスキル群

Cluster Toolkitには、インフラストラクチャスキルとワークロード固有スキルが新たに追加された。インフラストラクチャスキルは、計算・ストレージのクォータ監査や地域別キャパシティの事前チェックを行い、ワークロードに適したYAML形式のブループリントを自動でマッチングする。実際の`gcluster deploy`実行前には人間による承認を挟む設計になっており、自律実行ではなく人の確認を前提にしている点が特徴だ。ワークロード固有スキルは、流体力学分野のOpenFOAMやSiemens STAR-CCM+、生命科学分野のGROMACSやAlphaFold 3、地下資源シミュレーション分野のDevitoやOpen Porous Media(OPM)など、主要な科学計算ソフトウェアに対応する。さらに、IAMやKueueの割当、予算ガードレールといったガバナンス機能や、Cloud Loggingによる監査証跡、キューの停止やノードドレインへの自動対応を含むDay-2診断機能も備える。これらのスキルは、DeepMind Science Skills(github.com/google-deepmind/science-skills)とGoogle Skills(github.com/google/skills)という2つのリポジトリで公開され、自動エンドツーエンドテストを通過した検証済みテンプレートとしてダウンロードできる。

## AlphaEvolveのクラウド規模での実行

AlphaEvolveは、コードや3D設計パラメータを反復的に変異させ、ベンチマークを取りながら最適化を進める進化的最適化ループで、金融サービス、電子設計自動化(EDA)、製造業・物流、医薬品開発、AI訓練など幅広い分野での活用が想定されている。今回の拡張では、Cloud Batch上での並列実行がポイントとなり、単一VMまたはマルチノードMPI構成で数百の候補を同時評価できる自動並列評価、Pythonノートブックまたはコマンドラインからのインタラクティブ制御、そしてCloud RDMAやManaged Lustre、Spot VM・DWSを用いた本番スケールでの実環境検証が可能になった。Google Cloudは、ノートブック単体での試行から本番クラウド規模の最適化へ移行することで、以降のすべての実行における計算コストの削減につながるとしている。ただし具体的な性能改善の数値は記事中では示されていない。

## 基盤ハードウェアとSC26での展示

これらのソフトウェア機能を支えるハードウェア面では、第5世代AMD EPYCを搭載し3TBの高メモリ構成を取れるH4Dインスタンス(EDA向け)や、性能とワット効率を重視したArmベースのC4Aインスタンス(Google Axion)が用意される。GPU層では、結合物理AIやマルチノードGPU向けにNVIDIA Blackwell(B200/GB200 NVL72)を採用したA4/A4X、フロンティアAIの訓練・推論向けにNVIDIA Vera Rubin NVL72を新たにベアメタルで提供するA5X、CAE/CFDや3D可視化向けにNVIDIA RTX PRO 6000 Blackwellを使うG4が並ぶ。TPUでは第8世代が投入され、大規模事前学習や強化学習、数値シミュレーション向けのTPU 8tと、高スループット・低遅延の推論・エージェント推論向けのTPU 8iが単一ホストのTPUスライス単位で柔軟にプロビジョニングできる。ストレージ面では、読み取りスループット10TB/sでGPUDirect Storage over RDMAに対応するGoogle Cloud Managed Lustreや、80PB規模でCloud Storage Mirroringに対応するDynamic Tier、ローカルSSDキャッシュを活用するCloud Storage FUSEが用意されている。Google Cloudはシカゴの会場(McCormick Place West、ブース#3418)で、Antigravity for HPCやHPC Prompt Playground、AlphaEvolve for HPCのデモに加え、Advanced Computing Community Half-Day WorkshopやAgentic and Hybrid HPCに関するBirds of a Featherセッションを予定しており、エージェント型HPCの狙いを「未制御のモデルを野放しにすることではなく、Geminiの推論力とCluster Toolkitのスキル、Batch上の進化的最適化、専用ハードウェアを組み合わせ、チームがインフラ構築よりも発見に時間を割けるようにすること」だと説明している。
