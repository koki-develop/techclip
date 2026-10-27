---
date: "2026-10-28T08:08:08+09:00"
title: "Oracle、AI World 2026でSnowflakeをOCIにネイティブ統合、Cerebrasの推論専用ハードウェアも2027年導入へ"
description: "OracleはAI World 2026で、Snowflake AI Data CloudをOCIのファーストパーティサービスとして統合する計画と、Cerebras Systemsの推論向けハードウェアを2027年に導入する計画を発表した。"
tags:
  - Cloud
  - AI
references:
  - "https://www.oracle.com/news/announcement/ai-world-oracle-expands-native-ai-and-data-services-on-oci-with-snowflake-2026-10-27/"
  - "https://www.bloomberg.com/news/articles/2026-10-27/oracle-to-offer-cerebras-systems-computers-in-ai-cloud-service"
---

## 概要

Oracleはラスベガスで開催中の年次カンファレンス「Oracle AI World 2026」で、10月27日に2つの大型提携を発表した。1つはSnowflakeとの連携で、Snowflake AI Data CloudをOracle Cloud Infrastructure(OCI)上のネイティブなファーストパーティサービスとして提供する計画だ。もう1つはCerebras Systemsとの提携で、同社のウェーハスケールAIコンピューターをOCI上のAI推論基盤として2027年に導入するというもの。両提携はいずれも、OracleがNvidiaやIntelとの既存パートナーシップに加えて、AIインフラとデータ活用の選択肢を広げる狙いを示している。

## SnowflakeとのOCI統合

Snowflakeとの提携では、顧客がOracleと直接契約し、OCIの統一された課金・プロビジョニングを通じてSnowflake AI Data Cloudを利用できるようになる。Oracle Universal Creditsも適用可能で、プロビジョニングはOCIのコントロールプレーン経由で行い、その後は従来通りのSnowflakeの機能で運用する仕組みだ。

統合の目的は、Oracle Fusion Applications(ERP、HCM、SCM)やNetSuite、Oracle Autonomous AI Database、MySQL HeatWave、Oracle NoSQL DatabaseといったOracle上のエンタープライズデータに、Snowflakeの分析・AI機能をより近い場所で適用できるようにすることだ。クロスクラウドでのデータ移動とそれに伴うコストを削減しつつ、ガバナンス要件を満たしたままデータ活用を進められる点が特徴とされる。Snowflakeのプロダクト担当EVPであるChristian Kleinerman氏は、企業の意思決定が単一のアプリケーションのデータだけで完結することは稀だと指摘し、両社の連携によってヘルスケアや製造、小売、金融など複雑な業務課題に対応するAIアプリケーションの構築が可能になると説明している。主な対象は、すでにOCI上でFusionやNetSuite、Oracle Databaseを利用している既存のOracleエンタープライズ顧客になるとみられる。

## Cerebrasの推論ハードウェア導入

もう一方の発表は、AI半導体スタートアップのCerebras Systemsとの提携だ。CerebrasはシリコンウェーハをそのままAIプロセッサーとして使う独自の「ウェーハスケールエンジン」を手掛けており、通常は複数の小型チップに分割される一枚のウェーハを単一チップとして活用することで、チップ間のデータ移動や通信を減らし、長いコンテキストの推論処理や多段階のAIエージェントのワークフローにおけるトークン生成速度を高めるとしている。

Oracleは2027年前半からCerebrasのハードウェアをOCI上に展開する計画で、対象はAI研究機関や企業、インタラクティブなアプリケーションを開発するデベロッパーとされる。導入規模は明らかにされていない。OCI担当のMahesh Thiagarajan氏は、AI推論には選択肢が必要だと述べ、Nvidia向けGPUに加えてCerebrasのような専用アーキテクチャを用意する意義を強調した。CerebrasにとってはOpenAIやAWSに続く大型クラウド顧客の獲得となる。同社は2026年5月に上場しており、今回の提携を追い風に、現在10億ドル未満の年間収益を次年度には約30億ドルへ押し上げる見通しを示しているが、Nvidiaが圧倒的な市場シェアを持つ中でのポジショニングには投資家から懸念も残る。

## 展望

2つの発表は異なる領域を対象としているが、共通するのはOracleがOCIを「あらゆるデータとAIワークロードを引き寄せるハブ」として位置づけようとする姿勢だ。Snowflakeとの統合はデータ分析・ガバナンス面での顧客の選択肢を広げ、Cerebrasとの提携は推論の高速化という性能面での選択肢を広げる。両方とも具体的な提供開始時期や規模の詳細は今後明らかになる見込みで、実際の導入状況やOracle既存のNvidia・Intel向けインフラとの位置づけが今後の注目点となる。
