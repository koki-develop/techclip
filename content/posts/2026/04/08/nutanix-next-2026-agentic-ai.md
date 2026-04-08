---
date: "2026-04-08T10:38:28+09:00"
title: "Nutanix .NEXT 2026：エージェンティックAI対応プラットフォーム拡張とNetAppとの戦略的提携を発表"
description: "Nutanixは年次カンファレンス「.NEXT 2026」において、Agentic AI時代に向けたクラウドプラットフォームの大幅拡張、NetAppとの戦略的提携、およびサービスプロバイダー向け新プログラムを発表した。"
tags:
  - Cloud
references:
  - "https://www.globenewswire.com/news-release/2026/04/07/3269563/0/en/Nutanix-Delivers-Complete-Platform-for-the-Agentic-AI-Era.html"
  - "https://www.globenewswire.com/news-release/2026/04/07/3269564/0/en/Nutanix-Accelerates-Service-Provider-Growth-with-New-Cloud-Capabilities-and-Migration-Programs.html"
  - "https://www.globenewswire.com/news-release/2026/04/07/3269560/0/en/Nutanix-and-NetApp-Form-Strategic-Alliance-with-New-Integration-for-a-Modern-Cloud-Platform.html"
---

## 概要

Nutanixは2026年4月7日、シカゴで開催された年次カンファレンス「.NEXT 2026」において、Agentic AI時代を見据えたNutanix Cloud Platform（NCP）の大規模拡張を発表した。AI Agentワークロードの急増、複雑化するマルチクラウド環境、ハードウェア供給制約という三つの課題に同時対応する形で、インフラ全体でのAIエージェント実行を支援するエコシステム整備を推進する。30,000社以上の顧客基盤を持つNutanixが、VMwareからの移行需要を追い風にプラットフォームの包括性をさらに強化した格好だ。

## エージェンティックAI対応の新機能

今回の発表の中核を成すのが、**Nutanix Agentic AI Solution**（2026年後半GA予定）だ。仮想化・ストレージ・ネットワーク・Kubernetesサービスを統合したフルスタック基盤として設計され、企業がAI Factoryを構築するための包括的な基盤を提供する。GPUを多用するAIトレーニングワークロード向けには**NKP Metal**が新たに導入され、ベアメタルインフラ上で直接Kubernetesを実行できる。

ストレージ面では**Nutanix Unified Storage（NUS）5.3**がオブジェクトストレージの性能を向上させ、Google CloudやOVHCloudのS3へのSmartTiering拡張、RDMA加速（2026年後半予定）も追加された。データガバナンス・セキュリティ面では**Nutanix Data Lens 2.0**がオンプレミス完全対応となり、ランサムウェア分析機能を搭載。クラウド管理では**Nutanix Cloud Manager（NCM 2.0）**がすでにGAとなり、複数のPrism Central管理とコストガバナンス機能を統合している。

ハードウェアエコシステムの拡充も進む。現時点でDell PowerFlexの同期ディザスタリカバリおよびEverpure FlashArray //cに対応済みで、2026年後半にはAMD EPYC/Instinct GPU対応拡大、Cisco FlexPod統合、Dell PowerStore GA、Lenovo ThinkSystem統合、そしてNetApp ONTAPへの対応が予定されている。クラウド面ではNC2がAWS GovCloudへの対応を完了しており、AWS European Sovereign CloudおよびGoogle Cloud C3ベアメタルインスタンスへの展開も予定されている。

## NetAppとの戦略的提携

最も注目される発表の一つが、NetApp（NASDAQ: NTAP）との戦略的アライアンス締結だ。NetAppのIntelligent Data InfrastructureをNutanix Cloud PlatformおよびNutanix AHVハイパーバイザーと統合する取り組みで、NetApp AFFオールフラッシュAシリーズ、FASハイブリッドフラッシュシステム、NetApp ONTAPデータ管理ソフトウェアが対象となる。

統合ソリューションの主要機能として、NFSベース統合によるVM移行の高速化（数分単位でのインプレース変換）、NetApp ONTAP Autonomous Ransomware Protection with AI（ARP/AI）を活用したサイバーレジリエンス強化、そしてVM単位でのパフォーマンス・ストレージキャパシティ・リカバリを統合管理する一元ビューが挙げられる。さらに2026年後半には、NetApp ONTAPをNutanix Agentic AI Solutionのコンポーネントとして組み込む計画も進行中だ。Nutanixプレジデント兼チーフコマーシャルオフィサーのTarkan Maner氏は「顧客が各自のペースで近代化できるよう提携を進める」と述べ、段階的移行を重視する姿勢を示している。

## サービスプロバイダー向け施策とVMware移行支援

Broadcom によるVMware買収後の価格・ライセンス変更を受けて代替プラットフォームを模索するサービスプロバイダーを取り込む施策として、**Service Provider Central**（2026年後半GA予定）が発表された。複数顧客向けクラウドサービスを自動ワークフロー付きの単一管理画面から提供できるマルチテナント機能で、競争力のあるプライベートクラウドサービスを構築しやすくなる。

あわせて、ベストプラクティス準拠のサービス提供者を認証する**Powered by Nutanix: Verified Solutionsプログラム**（プライベートクラウド・IaaS・ディザスタリカバリを初期対象とし、将来的にDaaS・クラウドネイティブへ拡張予定）と、VMware移行期間中は名目的な月額費用でNutanixを利用可能にする**移行優遇プログラム**（3年以上のサブスクリプション契約対象）も提供される。これらの施策はVMware移行のコスト・リスクを軽減し、サービスプロバイダーのNutanix採用を加速させる狙いがある。

## 今後の展望

今回の発表群に共通するテーマは、NutanixがエージェンティックAI時代においてもコンピュートとストレージを独立してスケーリングできる柔軟なハイブリッド・マルチクラウド基盤を提供するという戦略的方向性だ。NetApp、Cisco、Dell、Lenovo、AMDなど主要ベンダーとのエコシステム連携を広げながら、ハードウェア供給制約下でも顧客が継続的にAI移行を進められる環境を整備する。Nutanix EVP（プロダクトマネジメント担当）のThomas Cornely氏が「顧客はハードウェアインフラを効率的に活用し、選択肢を維持できる」と強調するように、ベンダーロックイン回避とマルチクラウド選択の自由度を価値提案の核心に据えている。主要機能の多くは2026年後半のGAが予定されており、今後の実装とエコシステムの実績が問われることになる。
