---
date: "2026-09-16T18:14:05+09:00"
title: "Google Cloud、Pub/SubのAI Inference SMTが一般提供開始、ストリーミングデータにリアルタイム推論を付与"
description: "Google CloudがPub/SubにAI Inference Single Message Transformを一般提供し、ストリーミングイベントへのリアルタイムモデル推論適用と異常検知の簡素化を実現した。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/data-analytics/whats-new-with-google-data-cloud"
  - "https://docs.cloud.google.com/pubsub/docs/smts/ai-inference-smt"
---

## 概要

Google Cloudは9月10日、Data Cloudの最新アップデートの一環として、Pub/Subの「AI Inference Single Message Transform（SMT）」が一般提供（GA）になったことを発表した。これはPub/Subに流れ込む受信イベントストリームに対し、Gemini Enterprise Agent Platform上でホストされたモデルを用いてリアルタイムに推論を適用できる機能で、モデルの予測結果が元のメッセージに付加された状態でBigQueryなどのデータウェアハウスやBigTableのようなオペレーショナルデータベースへ渡せるようになる。Google Cloudはこの機能について、運用中の異常検知システムを大幅に簡素化・強化できるとしている。

## 仕組みと設定

AI Inference SMTはトピックまたはサブスクリプション単位で設定し、推論先のエンドポイントリソース名を指定する。自前でデプロイしたモデルの場合はAgent Platform上の公開エンドポイント（`projects/PROJECT/locations/LOCATION/endpoints/ENDPOINT`）を、Gemini・Claude・Llama・DeepSeek・QwenなどのMaaS（Model-as-a-Service）モデルを使う場合はパブリッシャーモデルのリソース名（`projects/PROJECT/locations/LOCATION/publishers/PUBLISHER/models/MODEL_NAME`）を指定する形式で、後者ならエンドポイント管理が不要になる。メッセージデータはターゲットモデルへのリクエストとして解釈可能なJSON文字列である必要があり、設定済みのモデルパラメータとマージされて推論リクエストが送信される。推論成功後は`original_message`と`model_output`を含むJSONとして元メッセージが拡張される。呼び出すAPIはモデルの種類によって異なり、自前デプロイモデルおよびGeminiの基盤モデル以外のGeminiモデル・Anthropic・Mistral AI・AI21モデルは`rawPredict`、Geminiの基盤モデルおよびLlama・DeepSeek・Qwenなどその他のMaaSモデルはChat Completions APIが使われる。

## 制約とコスト面

一方で現状は制約もある。1つのトピックまたはサブスクリプションにつきAI Inference SMTは1つまでしか設定できず、推論処理は60秒以内に完了する必要がある。バッチ推論やクライアント側でのバッチ処理には対応しておらず、あくまで1メッセージにつき1回の推論リクエストが基本となる。また変換後の最終的なメッセージサイズはPub/Subのメッセージサイズ上限内に収める必要がある。プライベートエンドポイントはサポート対象外で、自前デプロイモデルは必ずAgent Platformの公開エンドポイント上でホストされている必要がある。なお、SMTのテスト実行時にもAgent Platformモデルの呼び出しが発生するため、その分の利用料金が課金される点や、エンドポイント側のクォータ・レート制限の影響を受ける点にも注意が必要だ。

## 影響と展望

この機能により、これまでストリームプロセッサやカスタムのマイクロサービスを別途構築して行っていたリアルタイム推論の組み込みを、Pub/Subのパイプライン内で完結させられるようになる。特に不正利用検知やセンサーデータの異常検知など、レイテンシが重要な用途では、イベント受信からモデル推論、後段システムへの連携までを一気通貫で処理できる意義は大きい。Gemini系モデルに加えてClaudeやLlama、DeepSeek、Qwenなど複数ベンダーのモデルをMaaS経由で利用できる点も、既存のモデル運用資産を活かしたい企業にとって選択の幅を広げる要素となりそうだ。
