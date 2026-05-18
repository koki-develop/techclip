---
date: "2026-05-19T02:44:58+09:00"
title: "Cloud RunがNVIDIA RTX PRO 6000 Blackwell GPU対応をGA化、FirebaseはAIエージェントネイティブプラットフォームへ刷新"
description: "Google I/O 2026にてCloud RunがNVIDIA RTX PRO 6000 Blackwell GPUサポートとMCPサーバー機能を正式提供開始し、Firebaseはエージェントネイティブなプラットフォームへの進化を打ち出した。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/serverless/whats-new-for-cloud-run-at-next26"
  - "https://io.google/2026/explore/pa-keynote-13"
---

## Cloud Run：GPU対応とMCPサーバーが正式提供開始

Google I/O 2026に合わせて、Cloud Runに関する複数の重要なアップデートが発表された。最大の目玉は **NVIDIA RTX PRO 6000 Blackwell GPU対応のGA（一般提供開始）** だ。このGPUは70Bパラメータ以上の大規模言語モデルの推論に対応しており、Cloud Runのスケールゼロ機能と組み合わせることで、インフラ管理なしに使用量ベースの課金モデルで大規模モデルを本番運用できる。ElasticはCloud Runの使用量ベース・スケールゼロモデルへの移行によりアイドル時のGPUコストを削減し、17種類以上のモデルバリアントを本番環境で稼働させているという。Anthropicも、Cloud Runのサーバーレス・アーキテクチャによる即時スケーリングで急成長する需要に対応している顧客事例として紹介されている。

また、**Cloud Run MCPサーバー（Model Context Protocol）もGAとなった**。AIエージェントや開発者がコードをデプロイ・管理するためのツールとして機能し、エージェントと既存のクラウドインフラをつなぐ橋渡し役を担う。Google AI Studioとの連携強化も発表され、サーバーサイドコード・Firestoreデータベース・ユーザー認証を含むフルスタックアプリをGoogle AI Studio上で開発し、ワンクリックでCloud Runへデプロイする機能もGAとなった。Replit はすでに100万以上のライブプロジェクトをCloud Runでホストしており、VirginMedia O2 UKもAIカスタマーサービスツール「Lumi」でリアルタイム分析を実現している。

## エージェント実行基盤としての新機能群

AIエージェントの本番運用を支えるインフラ機能として、複数のプレビュー機能も公開された。**Cloud Run Instances**（プレビュー）は長時間稼働するバックグラウンドエージェントのホスティングを可能にし、gcloud CLIから作成できる。**Cloud Run Sandboxes**（近日提供）はエージェント用の高速かつ安全な隔離実行環境で、単一リクエスト処理中に即座に起動できる設計となっている。さらに、**Gemini Enterprise Agent Platform**との統合により、AIエージェントが実験環境から本番環境へ移行する際にインフラの再構築が不要になる（プレビュー）。

その他のプレビュー・近日提供機能として、Cloud RunコンテナへのSSHアクセス、月次最大支出を設定できる請求上限、インスタンスごとの一時ディスクストレージ（Ephemeral Disk）、マイクロサービス間通信を簡略化するCloud Run Service Bindingsなどが発表された。これらは総じて、Cloud RunをAIエージェントの本番実行基盤として強化する方向性を示している。

## FirebaseのAIエージェントネイティブプラットフォームへの進化

Google I/O 2026のセッションでは、**Firebaseが「エージェントネイティブなプラットフォーム」へと進化する方針**が示された。開発者がインテリジェントなアプリケーションを迅速に構築・スケールできる環境を整え、Google AI StudioやGoogle Antigravityとの統合により、プロトタイプから本番環境への移行が大幅に簡素化される。

この刷新により、Firebaseはモバイル・Webアプリのバックエンド基盤という従来の役割を超え、AIエージェントが動作するプラットフォームとしての位置づけを強めた。Google Cloudのインフラを基盤としたセキュリティとスケーラビリティを維持しながら、開発速度とAI統合の容易さを両立させることが狙いだ。Cloud RunのGPU対応やMCPサーバー機能と合わせると、GoogleがサーバーレスおよびFirebaseのエコシステム全体をAIエージェント時代向けに再設計している姿勢が明確に見える。
