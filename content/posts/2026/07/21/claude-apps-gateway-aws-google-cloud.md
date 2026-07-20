---
date: "2026-07-21T02:46:17+09:00"
title: "Anthropic、Claude Codeの企業導入を支える「Claude Apps Gateway」をAWS/Google Cloud向けに発表"
description: "AnthropicがAWSおよびGoogle Cloud向けの自己ホスト型ゲートウェイ「Claude Apps Gateway」を発表し、組織全体でのシングルサインオンとコスト管理を可能にした。"
tags:
  - Cloud
  - AI
references:
  - "https://www.publickey1.jp/blog/26/claude_codeclaude_apps_gateway_for_awsgoogle_cloud.html"
---

## 概要

Anthropicは2026年7月21日、AWSおよびGoogle Cloud向けに自己ホスト型のゲートウェイサービス「Claude Apps Gateway」を発表した。Claude Codeは個人利用であれば容易に導入できる一方、企業がエージェントを組織規模で展開しようとすると、社内アカウントとの統合やシングルサインオンの実装、利用状況の把握、従量課金コストの管理といった課題に直面していた。Claude Apps Gatewayは、こうした企業導入時の運用上のハードルを解消することを目的としたソリューションとなる。

## 主な機能

認証・アクセス制御の面では、OIDCに対応したIdPとの連携によりシングルサインオンを実現するほか、ロールベースアクセス制御(RBAC)のルールを「gateway.yaml」に記述して適用できる。このルールはローカル設定ファイル「managed-settings.json」よりも優先されるため、組織側が集中管理するポリシーを個々の端末設定に優先させることが可能だ。

コスト管理面では、組織・グループ・ユーザーそれぞれの単位で、日ごと・週ごと・月ごとの費用上限を設定できる。加えてテレメトリによる利用状況の把握や、推論リクエストのルーティングおよびフェイルオーバー機能も備えており、大規模導入時の運用監視とコスト最適化を同時に支援する仕組みとなっている。

## 対応バックエンドと技術構成

Claude Apps Gatewayは複数のAIモデルプロバイダをバックエンドとして選択できる点も特徴だ。Anthropic APIに加え、Amazon Bedrock、AWS上のClaude Platform、Google Cloud上のClaude、さらにMicrosoft Foundry上のClaudeにも対応する。サービス自体はマネージド型ではなく自己ホスト型として提供されており、組織は自社のインフラストラクチャ上でゲートウェイを運用できる。

## 企業導入における意義

セキュリティ、コンプライアンス、コスト最適化を一つのプラットフォームで統合的に管理できるようにすることで、Claude Codeをはじめとしたエージェント型ツールのエンタープライズ採用における障壁を下げる狙いがある。特に複数クラウド環境やモデルプロバイダを併用する組織にとっては、認証基盤とコスト管理を一元化できる点が導入判断の後押しになりそうだ。
