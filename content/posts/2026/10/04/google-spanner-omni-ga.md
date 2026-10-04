---
date: "2026-10-04T08:52:11+09:00"
title: "Google Cloud、分散DB「Spanner Omni」を正式リリース——オンプレ・マルチクラウドでも稼働可能に"
description: "Google CloudがSpanner技術をオンプレミスやマルチクラウド、ローカル環境でも利用できる「Spanner Omni」を正式リリースし、無償のDeveloper Editionと有償のCommercial Editionを用意した。"
tags:
  - Cloud
references:
  - "https://cloud.google.com/blog/products/databases/spanner-omni-deploy-anywhere-version-of-spanner-is-now-ga"
  - "https://www.publickey1.jp/blog/26/google_clouddbspanner_omni.html"
---

## 概要

Googleは9月30日、分散SQLデータベースSpannerの技術をGoogle Cloud以外の環境でも利用できるようにした「Spanner Omni」を正式リリースした。Spannerは10年以上前に分散SQLデータベース市場を切り拓いた製品だが、その後はリレーショナルなSQLに加えてグラフ、キーバリュー、全文検索、ベクトル検索、カラム型の分析処理までを単一のデータベースで扱えるマルチモデルDBへと進化してきた。Spanner Omniはこの機能群を、Paxosコンセンサスによる合意形成、自動シャーディング、同期レプリケーションといった基盤技術ごとそのまま持ち出し、単一サーバーから数千台規模のクラスタまでスケールさせ、ペタバイト級のデータとミリオン単位のクエリ毎秒（QPS）を処理できるようにしたものだ。プレビュー公開以降、累計200万回以上ダウンロードされているという。

## デプロイ先とライセンス体系

Spanner Omniはオンプレミスのデータセンター、複数クラウドにまたがるマルチクラウド環境、Kubernetes上のPod、さらには検証用にノートPC上のローカル環境にまでインストールでき、対応OSはLinux（RHEL 9、Ubuntu 22）とmacOS（M1、M2、M3）、Google CloudおよびAWSの仮想マシンにも及ぶ。ライセンスは2種類用意される。無償の「Developer Edition」は開発・テスト・プロトタイピング向けで、通常は90日間の試用期間付きだが、vCPU数が4以下の単一サーバー構成であれば期間無制限で利用できる（4vCPU超や90日超の利用延長はフォームからの申請で対応)。一方、商用・本番環境向けの「Commercial Edition」は業界標準的なvCPU数ベースの年間サブスクリプション課金で、エンタープライズサポートが付属するほか、割引価格のPoC（概念実証）ライセンスも用意されている。

## エンタープライズ機能とAIワークロードへの対応

エンタープライズ用途を見据え、TLS暗号化、認証・認可、監査ログ、高性能なバックアップ/リストア機能に加え、バックグラウンド処理や負荷の高い処理を主系サーバーから切り離して実行する専用のステートレスなワーカーノードを備える（このうちバックアップ/リストア機能はCommercial Edition、または4vCPU以下の単一サーバー構成のDeveloper Editionで利用可能。ワーカーノードはCommercial Editionのみで利用可能)。AIエージェント関連の機能も強化されており、ベクトル埋め込みをリレーショナルなテーブルと並べて格納・インデックス化しKNN/ANN検索を行えるベクトル検索とSpanner Graph、エージェント向けのトランザクショナルなメッセージングを行う「Spanner Queues」、さらにMCP Toolboxを介したModel Context Protocol(MCP)対応により、エージェントシステムからの利用を見込む。AIネイティブなCRMを手がけるAttioは、コンテナ化したSpanner OmniとマネージドSpannerを組み合わせてエージェント向けの本番環境に移行しており、同社の共同創業者兼CTOであるAlexander Christie氏は「Spanner Omniは、複雑でミッションクリティカルなワークフロー、特に新たに発表されたSpanner Queuesのようなものを本番環境に持ち込めるようにしてくれた点で、大きな勝利だった」とコメントしている。

## マネージドSpannerとの違いと展望

Spanner Omniはあくまで利用者自身がインフラを運用する形態であり、Google Cloud上のフルマネージドなSpannerのようなGoogleによる可用性SLAは提供されず、アップグレードなどの保守も利用者側の責任となる。BigQueryやGemini Enterpriseとのネイティブ連携といったGoogle Cloudとの統合も限定的だ。それでも、データ主権の要件から特定の国・地域の外にデータを出せない組織や、エッジに近い場所での低レイテンシ処理を必要とする組織にとっては、Spanner譲りの強整合性とスケーラビリティをオンプレミスやハイブリッド構成で得られる選択肢となる。クラウドネイティブなデータベースをどこでも動かせるようにする今回のリリースは、マルチクラウド・ハイブリッドクラウド化が進む企業のデータ基盤戦略に影響を与えそうだ。
