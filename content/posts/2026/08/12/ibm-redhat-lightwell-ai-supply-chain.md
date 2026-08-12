---
date: "2026-08-12T20:15:21+09:00"
title: "IBMとRed Hat、「Lightwell」を拡張しAI時代のOSSサプライチェーンに信頼基盤を構築"
description: "IBMとRed HatがOSSプラットフォーム「Lightwell」を拡張し、Sigstore・in-toto・SLSA・SBOMを統合した商用サービスとしてAI時代のソフトウェアサプライチェーンの署名・来歴検証・ポリシー管理を強化した。"
tags:
  - OSS
  - Security
references:
  - "https://www.infoq.com/news/2026/08/lightwell-ai-open-source/"
---

## 概要

IBMとRed Hatは7月8日、オープンソースのソフトウェアサプライチェーン基盤「Lightwell」を拡張し、新たに商用サービスを提供開始したと発表した。今回の拡張は、Sigstore・in-toto・SLSA（Supply-chain Levels for Software Artifacts）・SBOM（Software Bill of Materials）といった既存のセキュリティ標準を個別の機能としてではなく、単一の統合プラットフォームとして組み合わせる点が特徴で、ソフトウェア配送プロセスの各段階を検証可能にすることを目指している。背景には、AI生成コードの混入やOSSサプライチェーンを狙った攻撃への懸念の高まりがあり、両社は「コードをより速く生成すること」自体はもはや課題ではなく、「ソフトウェアがどこで生まれ、どのようにビルドされ、改変されていないか、組織のセキュリティポリシーに準拠しているかを証明すること」こそが課題だと位置づけている。

## 技術的な詳細

商用版Lightwellが提供する主要機能は、アーティファクトの署名、来歴（provenance）情報の生成、ポリシー検証、そしてライフサイクル管理の4つに整理される。Sigstoreによる署名基盤とin-totoによるビルド来歴の記録、SLSAが定めるサプライチェーンの成熟度レベル、SBOMによる構成要素の可視化を組み合わせることで、開発から本番デプロイに至るまでの各段階で「何が」「誰によって」「どのように」作られたかを追跡・検証できる仕組みを構築している。これにより、AIが生成したコードが混入した場合でも、その出所や改変履歴を後から確認できる体制を整えている。

## 背景と業界の動き

今回の取り組みは、GitHub・Google・Microsoft・Cloud Native Computing Foundation（CNCF）が進める検証可能なソフトウェアサプライチェーンへの取り組みとも軌を一にする。GitHubはCodeQLやアーティファクト証明（attestation）、シークレットスキャンなどの機能を提供しており、GoogleはSLSAフレームワークの採用を推進、MicrosoftはAzure DevOpsとGitHub Advanced Securityの統合を進めている。またCNCFはセキュリティ企業Kusariと連携しており、Linux FoundationもAI由来の脅威からOSSを守る「Akrites」プロジェクトを立ち上げるなど、業界全体でAI時代のソフトウェアの信頼性確保に向けた動きが広がっている。

## 今後の展望

IBMとRed Hatは、企業がAI生成コードへの依存を強めるにつれて、検証可能な「信頼インフラ(trust infrastructure)」の構築が基盤的な能力になっていくと見ている。人間の開発者だけでなく、ソフトウェア開発に関与するAIシステムそのものについても信頼性を担保する必要があるという認識が広がりつつあり、ソフトウェアのライフサイクル全体を通じて来歴を検証可能にする取り組みは、今後さらに重要性を増していくとみられる。
