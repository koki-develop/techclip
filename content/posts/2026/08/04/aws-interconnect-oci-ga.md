---
date: "2026-08-04T20:42:04+09:00"
title: "AWS Interconnect、Oracle Cloud Infrastructure接続が一般提供開始 マルチクラウド接続を簡素化"
description: "AWSはマルチクラウド接続サービス「AWS Interconnect」のOracle Cloud Infrastructure対応を一般提供開始し、Google Cloudに続く2番目の対応クラウドとなった。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/07/aws-announces-AWS-interconnect-multicloud-OCI-GA/"
---

## 概要

AWSは7月29日、複数のクラウドプロバイダー間をプライベート接続するサービス「AWS Interconnect」について、Oracle Cloud Infrastructure（OCI）対応を一般提供（GA）開始したと発表した。OCIは5月から公開プレビューとして先行サポートされており、今回正式にGAへ移行した形となる。AWS Interconnectとしては、既に対応済みのGoogle Cloudに続き2番目のマルチクラウド接続先となる。AWSは、複数のクラウドサービスを個別に組み合わせて接続を構築する「DIY型マルチクラウド」の複雑さを排除することを本サービスの狙いとして説明している。

## 技術的な詳細

AWS Interconnectはオープン仕様に基づいて構築されており、その仕様はGitHub上で公開されている。ユーザーはAWS Management Console、CLI、APIのいずれからでも接続を設定できる。現時点でのサービス提供リージョンはus-east-1（バージニア北部）のみとなっており、他リージョンへの展開時期は今回の発表では明らかにされていない。なお、具体的な料金体系やユースケースの詳細については、今回のアナウンスメントには記載がなく、公式ドキュメントの参照が推奨されている。

## 今後の展望

AWSはMicrosoft Azureについても2026年後半にAWS Interconnect対応を追加する計画を明らかにしている。これが実現すれば、AWS Interconnectは主要3大クラウド（Google Cloud、OCI、Azure）すべてとのプライベート接続をサポートすることになり、複数クラウドにまたがるワークロードを運用する企業にとって、クラウド間のネットワーク構築を大幅に簡素化する選択肢となりそうだ。
