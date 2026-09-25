---
date: "2026-09-26T08:10:50+09:00"
title: "Azure Container Apps SandboxesとExpressが正式GA、マイクロVM分離でエージェント実行基盤を強化"
description: "MicrosoftはAzure Container Apps SandboxesとACA Expressの一般提供を開始し、マイクロVM分離による安全なコード実行とサーバーレスの高速起動を両立した。"
tags:
  - Cloud
references:
  - "https://techcommunity.microsoft.com/blog/appsonazureblog/azure-container-apps-sandboxes-now-generally-available/4559125"
  - "https://www.beyondcloudwithchriz.com/post/azure-container-apps-sandboxes-reaches-ga-egress-state-and-audit-controls-matter"
  - "https://learn.microsoft.com/en-us/azure/container-apps/express-overview"
  - "https://sandboxes.azure.com/docs/sandboxes/"
---

## 概要

Microsoftは2026年9月23日、Azure Container Apps(ACA)の新しい実行基盤である「ACA Sandboxes」と、サーバーレスデプロイの新モデル「ACA Express」の一般提供(GA)を発表した。両者はプレビュー期間を経て正式版となり、エージェントワークロードと高速なWebアプリ配信という異なる要求に応える形で設計されている。ACA Expressはコンテナイメージから本番稼働までを最速で実現するデプロイモデルであり、その高速な起動とスケーリングを支える計算基盤として、ACA Sandboxesのマイクロ VM分離技術を採用している。ACA SandboxesはExpressだけでなく、GitHub Copilotのクラウドサンドボックスや Foundry Hosted Agentsなど、Microsoft社内の複数の製品がすでに基盤として利用しているという。

## マイクロVM分離とサンドボックスの管理機能

ACA Sandboxesは、Azure Resource Manager(ARM)上のリソースである「サンドボックスグループ」として管理され、1グループに数千単位のサンドボックスをオンデマンドで含められる。各サンドボックスはディスクイメージから起動し、独自のカーネルと仮想ハードウェアを持つ「ハードウェア隔離されたマイクロVM」として実行され、CPU仮想化によってメモリ分離を強制する。これにより、信頼できないコードやマルチテナントのタスクを、強い分離境界の中で安全に実行できる。

ネットワーク制御は組み込みのエグレスプロキシが担う。ポリシーを設定しない場合、サンドボックスは無制限のアウトバウンドアクセスを持つため、既定拒否のポリシー、パスやメソッドによるマッチング、リクエスト変換、ルールの順序評価といった機能はすべてオプトインで有効化する設計になっている。状態管理も柔軟で、ディスク状態のみを保持する「停止」状態、ディスクとメモリの両方を保存するスナップショット、サンドボックス削除後も存続する永続ボリュームなど、複数の永続化オプションから選択できる。監査・テレメトリ機能(コンソール出力、OpenTelemetry信号、運用メトリクス、エグレス決定ログ)も作成時に明示的な設定が必要なオプトイン方式であり、ログ記録自体はポリシーの強制とは別機能である点に注意が必要だとされる。

## ACA Expressによる高速デプロイ

ACA Expressは、環境のプロビジョニングを待たずにコンテナアプリを直接作成できる、開発者およびエージェント向けの高速デプロイモデルだ。消費ベースのコンピュートで動作し、リクエストに応じてゼロからハイパースケールまで自動的にスケールし、アイドル時はゼロまでスケールダウンするため使用した分だけ課金される。環境プロビジョニング費用は発生せず、毎月最初の180,000 vCPU秒、360,000 GiB秒、200万リクエストは無料枠として提供される。コールドスタートからの起動はサブセカンドまで最適化されており、SaaSアプリケーションやAIアプリのフロントエンド、開発者向けツール、社内ダッシュボード、スタートアップの迅速なプロトタイピングといった用途に適する。

一方でExpressはHTTP中心のワークロードに特化しており、GPUワークロード、TCPサービス、ジョブ/バッチ処理、サービスディスカバリを伴うマイクロサービスといった用途には非対応で、それぞれ既存のサーバーレスGPUやワークロードプロファイル環境、Container Apps Jobsが代替手段として案内されている。HTTP/2やDapr、カスタムドメイン、OpenTelemetryといった機能も現時点ではサポート対象外だ。提供リージョンは日本(East/West)を含む40以上のAzureリージョンに及ぶ。

## 展望

ACA SandboxesはすでにGitHub CopilotのクラウドサンドボックスやFoundry Hosted Agentsの基盤として採用されており、Expressと合わせて一般提供されたことで、エージェント実行基盤としての実運用への採用が本格化するとみられる。マイクロVMによる強い分離と、サブセカンドの起動・スケーリングという両立が難しかった要件を単一の基盤で満たす設計は、今後増加が見込まれる自律型AIエージェントのマルチテナント実行や、信頼できないコードを大量に処理するサービスにとって、有力な選択肢になりそうだ。
