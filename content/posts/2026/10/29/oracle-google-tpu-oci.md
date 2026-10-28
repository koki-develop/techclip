---
date: "2026-10-29T08:08:19+09:00"
title: "OracleがGoogleのTPUをOCIに導入、ハイパースケーラー初の提携でAI基盤を多様化"
description: "OracleがOracle AI WorldでGoogleのTPUをOracle Cloud Infrastructureに導入する提携を発表し、ChatGPT統合サービスも併せて展開する。"
tags:
  - Cloud
  - AI
references:
  - "https://siliconangle.com/2026/10/27/oracle-brings-googles-tpus-to-its-cloud-adds-chatgpt-integrations/"
---

## 概要

Oracle AI WorldにおいてOracleとGoogle Cloudは、GoogleのTPU(Tensor Processing Unit)をOracle Cloud Infrastructure(OCI)で提供する提携を発表した。Googleが自社以外のハイパースケーラーにTPUを供給するのは今回が初めてで、提供開始は2027年から、容量は段階的に拡大していく計画だ。OracleはすでにNVIDIA製GPUを主力とするAI基盤を展開しているが、今回の提携によってGoogle製のTPUという選択肢も加わり、顧客のワークロードに応じたアクセラレータの多様化が進む。

## 技術的な詳細

TPUの接続にはGoogle独自のインターコネクト技術である光学方式の「OCS」と銅線方式の「ICI」が用いられる。これをOracleのデータセンター全体のネットワークに統合するのが、同社の「Acceleron」ネットワーキング技術だ。Acceleronは独自開発のSmartNICチップによって駆動され、ネットワーク管理とセキュリティ機能を担う。Oracleのシニアバイスプレジデントであるカラン・バッタ氏とGoogle Cloudのシニアディレクターであるグルミート・ゴインディ氏は、「AcceleronのSmartNICはハードウェアレベルのテナント分離、高性能ファブリック、ゼロトラスト・パケットルーティングを備え、高いスループットと低レイテンシでデータを転送する」と説明している。Oracleは今回のTPUに加え、Cerebras Systemsの数兆個のトランジスタを搭載するウェーハスケール・アクセラレータや、OpenAIの推論用プロセッサ「Jalapeño」(8月の発表によれば競合製品より1.5倍高速)もOCIに展開する計画で、GPU一強だったAI基盤に複数のアクセラレータを並存させる方針を明確にしている。

## ChatGPT統合サービスの拡充

Oracleは同時に、OpenAIのChatGPTと自社クラウドサービスを連携させる複数の新サービスも発表した。「AI Workspace」はOracleのクラウドアプリケーションとChatGPTを統合し、チャットボットが業務タスクの実行や外部アプリケーションとの連携を行えるようにする。「App Composer」は技術者でなくてもAIアプリケーションを構築できるツールで、脆弱性スキャンの自動化やクラウド環境への展開管理も備える。セキュリティ面では、OpenAIのセキュリティ向けモデルを用いて脆弱性を特定し深刻度別に修正案を提示する「AI Security Mesh」も用意される。さらに中小企業向けには、年間1万2000ドル分のクラウドクレジットを無償で提供する「Oracle AI SMB Bundle」も導入される。

## 展望

今回の発表は、特定のGPUベンダーへの依存を避けつつAI基盤の選択肢を広げるというOracleの戦略を示すとともに、OpenAIの技術を企業の業務自動化に積極的に取り込む姿勢も表している。GoogleにとってはTPUを他のハイパースケーラーに供給する初の事例となり、NVIDIA GPU中心のAIインフラ市場に新たな競争軸をもたらす可能性がある。2027年のサービス開始に向け、各アクセラレータの性能や価格競争力、顧客の採用動向が今後の焦点となりそうだ。
