---
date: "2026-04-20T02:17:42+09:00"
title: "AWSが複数サービスの段階的廃止を発表——App Runnerは4月30日に新規受付停止"
description: "AWSがAWS App Runnerを2026年4月30日より新規受付停止・メンテナンスモードへ移行すると発表し、Amazon RDS Custom for OracleやAmazon WorkMailなど複数のサービスも段階的廃止が予定されている。"
tags:
  - Cloud
references:
  - "https://www.publickey1.jp/blog/26/aws_app_runner430amazon_rds_custom_for_oracle1aws.html"
---

## 概要

AWSは、複数のサービスについて新規受付停止および段階的廃止の計画を相次いで発表した。最も早い対応が必要となるのはAWS App Runnerで、2026年4月30日をもって新規利用登録が停止される。その後はメンテナンスモードへ移行し、既存ユーザーは引き続きサービスを利用できるものの、新機能の追加や機能強化は行われない。利用中のユーザーには代替サービスへの移行計画を早期に立てることが求められる。

## 対象サービスと廃止スケジュール

廃止が発表されたサービスはApp Runnerにとどまらず、完全終了（サンセット）となるサービスも複数含まれる。**Amazon RDS Custom for Oracle**は2027年3月31日にサポートを終了する予定で、SSH経由でのインフラアクセスやカスタムパッチ・バックアップ運用が可能だったこのサービスの利用者は、AWSが提供する公式ドキュメントの移行ガイドを参照して対応が必要となる。

メンテナンスモードへ移行するサービスには、以下が含まれる（AWS CloudTrail Lakeはすでに2026年3月31日に新規登録を停止済み）。

- AWS CloudTrail Lake
- AWS Audit Manager
- AWS IoT FleetWise
- Amazon Comprehend（一部機能）
- Amazon Rekognition（一部機能）
- SNS Message Data Protection
- Application Recovery Controller Readiness Check

さらに完全廃止（サンセット）が予定されているサービスとして、**Amazon WorkMail**・**Amazon WorkSpaces Thin Client**・**AWS Service Management Connector** の3つが挙げられている。

## 移行先と今後の対応

AWS App Runnerからの推奨移行先として、AWSは2025年12月にリリースされた**Amazon ECS Express Mode**を提示している。ECS Express Modeはマネージドコンテナサービスとして、App Runnerが提供していたシンプルなコンテナデプロイ体験を引き継ぐ位置づけとなる。Amazon RDS Custom for Oracleについても、公式ドキュメント上で移行パスの選択肢が案内されている。

今回の一連の発表は、AWSがポートフォリオの整理を進めていることを示す動きとも言える。利用中のサービスが対象に含まれている場合は、廃止タイムラインを確認した上で、代替サービスへの移行計画を早期に策定することが重要だ。
