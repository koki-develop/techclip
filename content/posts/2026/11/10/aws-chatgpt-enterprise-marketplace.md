---
date: "2026-11-10T18:09:28+09:00"
title: "OpenAI、ChatGPT EnterpriseをAWS Marketplaceに出品 クラウド利用コミットメントに充当可能に"
description: "OpenAIがChatGPT EnterpriseをAWS Marketplace経由で購入可能にし、対象支出をAWSのEDPやPPAなどのクラウド利用コミットメントに充当できるようにした。"
tags:
  - Cloud
  - AI
references:
  - "https://ppc.land/aws-customers-can-now-buy-chatgpt-enterprise-against-cloud-commitments/"
  - "https://openai.com/index/chatgpt-enterprise-aws-marketplace/"
---

## 概要

OpenAIは11月9日、ChatGPT EnterpriseをAWS Marketplace経由で購入できるようにしたと発表した。対象となるのはChat(対話型AI)、ChatGPT Work(複数ステップの調査・分析・文書作成を行うエージェント)、Codex(コードベースの理解やバグ修正、テスト実行を担うコーディングエージェント)、dots(ユーザーの好みを学習し継続的な業務を管理する常時稼働エージェント)の4製品を含むバンドルで、既存のAWS購買・請求関係を通じてそのまま調達できる。

今回の対応の最大のポイントは、ChatGPT Enterpriseへの支出が、企業がAWSと結ぶEnterprise Discount Program(EDP)やPrivate Pricing Agreement(PPA)といった複数年のクラウド利用コミットメントの消化対象になることだ。EDPやPPAは、企業が一定期間にわたる最低支出額をAWSに対して約束する代わりに割引を受けられる契約形態であり、個々の顧客契約の内容次第ではあるものの、ChatGPT Enterpriseの利用料をその消化に充てられるようになる。これにより、企業は新たな調達プロセスを追加せずに既存のAWS予算の枠内でChatGPTを導入できる。AWS Marketplaceのパートナーサービスを統括するVPのMatt Yanchyshyn氏は「企業は新たな調達の手間を増やすことなく、AIを各チームで活用できるようにしたいと考えている」と述べている。

## Claude Enterpriseとの競合

ChatGPT Enterpriseは今回、同じAWS Marketplace上で以前から提供されているAnthropicのClaude Enterpriseと直接競合する形になった。Claude Enterpriseも同様にコミットメントの消化に対応しており、両社の主力エンタープライズ製品がAWSの購買チャネル上で並び立つことになる。Anthropicにとってマーケットプレイス経由の販売は既に大きな収益源となっており、2026年の9か月間の収益のうち約44%をクラウドマーケットプレイス経由の売上が占めているという。OpenAIの参入により、クラウド経由のAI販売チャネルでの競争が一段と激しくなる見通しだ。

なお、ChatGPT Enterpriseの価格はAWS Marketplaceの出品ページ上では公開されておらず、「カスタム価格オプション」として個別見積もり(プライベートオファー)の申請が必要な形になっている。AWS側の手数料や利用量の算出方法についても詳細は明らかにされていない。

## 背景と今後

今回の発表は、OpenAIのモデルがAmazon Bedrock上で利用可能になった流れを引き継ぐものだ。Bedrockでは2026年4月28日に限定プレビューが始まり、6月1日に一般提供が開始されている。ChatGPT EnterpriseのAWS Marketplace出品は、こうしたAWSとOpenAIの協業を調達・契約面にまで広げる動きと位置づけられる。一方で、AWS Marketplace経由で購入した場合の対応リージョンや国ごとの利用可否、データ保存地域などの詳細、またOpenAIと直接契約する場合との違いについては、現時点で明らかにされていない。
