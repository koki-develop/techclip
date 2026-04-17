---
date: "2026-04-18T02:23:43+09:00"
title: "OracleとAWSが専用プライベート接続で協業、マルチクラウドネットワークが本格化"
description: "OracleとAWSは2026年4月16日、OCI・AWS間でパブリックインターネットを迂回する高速プライベート接続を提供する計画を発表し、マルチクラウドネットワーキングの普及に向けた取り組みが加速している。"
tags:
  - Cloud
references:
  - "https://www.oracle.com/news/announcement/oracle-and-aws-collaborate-to-expand-multicloud-networking-2026-04-16/"
  - "https://siliconangle.com/2026/04/16/best-frenemies-oracles-awss-clouds-unite-dedicated-private-connectivity/"
  - "https://www.techtarget.com/searchcloudcomputing/news/366641818/Multi-cloud-networking-gains-momentum-with-aws-and-oracle"
---

## 概要

OracleとAWSは2026年4月16日、Oracle Cloud Infrastructure（OCI）とAWS間でパブリックインターネットを経由しない高速プライベート接続を確立する計画を発表した。「Oracle Interconnect」と「AWS Interconnect–multicloud」を相互接続する形で実現し、まずAWS米国東部（バージニア北部、`us-east-1`）リージョンで2026年内の提供開始を目指す。両社は長年にわたりクラウド市場での競合関係にあったが、エンタープライズ顧客のマルチクラウド需要の高まりを受けて協業に踏み切った形だ。

OCI側のプロダクト管理SVPであるNathan Thomas氏は「当社のクロスクラウドインターコネクトとAWS Interconnect–multicloudの間に接続を確立し、クロスクラウド接続機能をAWSへ拡張する。顧客のアプリケーション近代化、データ統合、そして新たな生成AIの機会開拓を支援する」と述べた。

## 技術的な詳細

今回の接続は最大100 Gbpsの帯域幅を提供するフルマネージドのエンタープライズグレード接続で、自動冗長化とロードバランシング、協調サポートモデルを備える。アーキテクチャ上はフルスタックとスプリットスタックの両形態のマルチクラウド展開に対応しており、アプリケーションとデータを異なるクラウドに分散配置するケースにも利用できる。

AWS側では2026年4月14日に「AWS Interconnect–multicloud」が一般提供（GA）に移行しており、AWS Transit GatewayやAWS Cloud WANとの統合により複数のVPCやリージョンへの迅速なスケーリングが可能だ。クラウドプロバイダーはGitHub上で公開されているオープン仕様のAPIを通じて参加できる。料金体系はOCI側では出力・帯域費用は発生せず、ポートおよび仮想回線の速度に応じた費用のみとなる。AWS側は帯域域幅と地理的範囲に基づく一律料金で、2026年5月からは1リージョンあたり500 Mbpsの無料枠も提供される。なお、超低レイテンシが求められるトランザクション系ワークロードには適していないと明示されている。

## 背景とマルチクラウド戦略の潮流

今回の発表は2025年に開始した「Oracle AI Database@AWS」（OracleのデータベースワークロードをAWS内で実行するサービス）をベースにした取り組みの延長線上に位置づけられる。OracleはすでにGoogle CloudおよびMicrosoft Azureとのインターコネクトを確立しており、AWSとの接続によって主要クラウド3社すべてとのプライベート接続網が完成する見込みだ。AWS側でもGoogle Cloud（2025年12月）に続く接続パートナー追加となり、Microsoftとのパートナーシップも2026年中に予定されている。

theCUBE ResearchのアナリストRob Strechay氏は「2つの最大規模のクラウドドメイン間のネットワーク複雑性を排除することで、企業のクロスクラウドレジリエンスとAIアーキテクチャの実現可能性が大幅に向上する。AIの未来はデータが一方のクラウドに存在し、モデルが別のクラウドで動作し、ネットワークが妨げにならない世界にある」と評価する。一方で、接続が容易になってもデータエグレス費用は依然として発生するため、実際のコスト試算には注意が必要だと指摘する声もある。

## 今後の展望

本接続の提供開始によって、AIワークロード、大容量データ転送、ディザスターリカバリーといったユースケースでのマルチクラウド活用が現実的な選択肢になる。Constellation ResearchのHolger Mueller氏は「OCIとAWSのクラウド間でデータ交換を容易かつ効率的にセットアップできる手段として、多様なユースケースを支える基盤となる」と述べており、エンタープライズ向けのマルチクラウド戦略が新たな段階に入りつつあることを示している。
