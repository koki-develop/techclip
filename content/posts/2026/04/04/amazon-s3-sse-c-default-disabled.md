---
date: "2026-04-04T02:16:45+09:00"
title: "Amazon S3、2026年4月6日より新規バケットでSSE-Cをデフォルト無効化——SSE-KMSへの移行を推奨"
description: "AWSはAmazon S3の新規バケットおよびSSE-C暗号化オブジェクトを持たない既存バケットを対象に、カスタマー提供キーによるサーバーサイド暗号化（SSE-C）を2026年4月6日からデフォルトで無効化すると発表した。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/blogs/storage/advanced-notice-amazon-s3-to-disable-the-use-of-sse-c-encryption-by-default-for-all-new-buckets-and-select-existing-buckets-in-april-2026/"
---

## 概要

AWSは2026年4月6日より、Amazon S3のカスタマー提供キーによるサーバーサイド暗号化（SSE-C）を新規バケットに対してデフォルトで無効化する。さらに、AWSアカウント内にSSE-Cで暗号化されたオブジェクトが存在しない既存バケットも同様の変更対象となる。一方、SSE-C暗号化オブジェクトを保有するバケットは引き続きSSE-Cをサポートし続けるため、現行の運用に即座の影響はない。この変更は4月6日以降、数週間かけて全AWSリージョンへ展開される予定だ。

## 技術的な変更内容

変更後、新規バケットの `GetBucketEncryption` APIレスポンスには `BlockedEncryptionTypes` に `SSE-C` が含まれるようになる。SSE-Cが無効化されたバケットへSSE-Cを指定してオブジェクトをアップロードしようとすると、HTTP 403 Access Deniedエラーが返される。

SSE-Cが必要なバケットでは、`s3:PutEncryptionConfiguration` 権限を持つユーザーが `PutBucketEncryption` APIを呼び出してSSE-Cを明示的に有効化する必要がある。既存のCloudFormationテンプレートや自動化スクリプトがSSE-Cを前提としている場合は、事前に設定の見直しが求められる。

## 背景：SSE-CからSSE-KMSへ

SSE-Cは2014年6月にAmazon S3へ追加された機能で、顧客が暗号化キーを自分で管理できる仕組みとして提供された。しかし同年11月にAWS Key Management Service（AWS KMS）がリリースされて以降、SSE-Cの実用的な優位性は薄れてきた。

AWS KMSを使うSSE-KMSでは、きめ細かなIAMポリシーによるキーへのアクセス制御や、AWS CloudTrailによるキー操作ログの取得が可能だ。また、データを読み書きするユーザー・ロール・AWSサービスに対して、実際のキーを渡すことなくアクセス権を付与・剥奪できる。一方SSE-Cでは、S3がキーを保存しない設計上、SSE-C暗号化データへアクセスするたびに暗号化キーを都度提供しなければならず、複数のユーザーやサービスとの共有が現実的ではない。現在すでに数十万の顧客がSSE-KMSを採用しており、AWSは今回の変更を通じて暗号化オプションをより分かりやすく整理する狙いがあるとしている。

## SSE-KMSで対応できないケースへの対処

Parquetファイル内の特定のカラムチャンクを異なるキーで暗号化するなど、SSE-KMSでは実現できない高度な要件がある場合は、クライアントサイド暗号化の活用が推奨されている。AWSはオープンソースの **AWS Encryption SDK** および **S3 Encryption Client** ライブラリを提供しており、AWS KMSや独自のキー管理ソリューションと組み合わせて利用できる。現在SSE-Cを使用しているかどうかは、CloudTrailによるアクセス監査やS3 Inventoryレポートのクエリで確認可能だ。
