---
date: "2026-06-28T02:28:19+09:00"
title: "AWSがAIエージェント向けサーバーレス実行環境「Lambda MicroVMs」を発表、Firecrackerで最大8時間のVM分離を実現"
description: "AWSはFirecracker技術を活用したサーバーレスコンピュート機能「Lambda MicroVMs」を発表し、AIエージェントやユーザー生成コードを最大8時間、VM レベルで安全に実行できる環境を提供する。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/blogs/aws/run-isolated-sandboxes-with-full-lifecycle-control-aws-lambda-introduces-microvms/"
  - "https://aws.amazon.com/about-aws/whats-new/2026/06/aws-lambda-microvms/"
  - "https://www.theregister.com/devops/2026/06/23/aws-debuts-lambda-microvms-with-up-to-8-hours-runtime/5260035"
---

## 概要

AWSは2026年6月22日、新しいサーバーレスコンピュート機能「Lambda MicroVMs」を発表した。本機能はAIエージェントやユーザーが生成したコードを、管理されたインフラを必要とせずにVMレベルの強力な分離環境で実行するために設計されている。従来のLambda Functionsが最大15分の実行時間に制限されていたのに対し、Lambda MicroVMsでは最大8時間のステートフルな実行が可能となっており、AIコーディングアシスタントやインタラクティブなコード実行環境といった長時間稼働が前提のワークロードに適している。

基盤技術として採用されているのは、AWSが自社で開発した軽量VMM（仮想マシンモニター）のFirecrackerだ。同技術はすでに月間15兆回以上のLambda関数呼び出しを支えており、コンテナと比較してより強固なカーネルレベルの分離を実現する。AWSはプロンプトインジェクション対策や悪意あるパッケージの検査、脆弱性スキャンといった「信頼できないコードの実行」シナリオを主要なユースケースとして挙げている。

## 技術的な詳細

Lambda MicroVMsの各インスタンスは最大16 vCPU・32GBメモリ・32GBディスクを利用でき、ARM64（AWS Graviton）アーキテクチャ上で動作する。各MicroVMには専用のHTTPSエンドポイントが割り当てられ、HTTP/2・gRPC・WebSocketプロトコルをサポートする。

起動高速化の仕組みとして、Dockerfileとコードアーティファクトから作成した「MicroVM Image」を事前にスナップショット化しておくことで、以降の起動はほぼ瞬時に行えるよう設計されている。MicroVMはアイドル時に一時停止（サスペンド）し、リクエスト到着時に自動再開（レジューム）する構成を取ることができ、メモリ・ディスク・実行中のプロセスがセッションをまたいで保持される。アイドルポリシーは開発者が設定可能で、自動一時停止までの時間や自動再開の有効化を制御できる。

料金体系はベースラインリソース使用時に課金される形式で、一時停止中はスナップショットのストレージコストのみが発生する。デプロイはDockerfileベースのカスタムイメージを作成後、AWSコンソール・CloudFormation・CDK・Agent Toolkitを通じて行える。

## 既存Lambda Functionsとの関係とユースケース

Lambda MicroVMsはLambda Functionsの代替ではなく、補完的なサービスとして位置づけられている。イベント駆動型のシンプルな処理は引き続きLambda Functionsが担い、信頼できないコードの安全な実行や長時間のインタラクティブセッションが必要な場面でMicroVMsを組み合わせる設計が想定されている。

AWSが挙げる主な利用シナリオは次のとおりだ。AIコーディングアシスタント、インタラクティブなコード実行環境、データ分析プラットフォーム、脆弱性スキャナー、ユーザー提供スクリプトを実行するゲームサーバーなどが含まれる。開発者コミュニティからは、フルシェルアクセスやHTTP ingressを活用したCI/CDへの組み込みや、AIエージェントの長時間実行基盤としても注目を集めている。現時点での提供リージョンは米国東部（バージニア北部・オハイオ）、米国西部（オレゴン）、ヨーロッパ（アイルランド）、アジア太平洋（東京）の5リージョンとなっている。
