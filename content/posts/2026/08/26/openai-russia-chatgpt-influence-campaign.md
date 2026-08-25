---
date: "2026-08-26T08:05:07+09:00"
title: "OpenAI、偽シンクタンクで権威を装いChatGPTを悪用したロシア発の世論工作を摘発"
description: "OpenAIはChatGPTを使い架空のシンクタンク「International Burke Institute」を装って親ロシア的な言説を拡散していたロシア発のアカウント群を特定し、停止したと発表した。"
tags:
  - AI
  - Security
references:
  - "https://www.cnbc.com/2026/08/25/openai-russia-chatgpt-influence-campaign.html"
  - "https://www.tradingview.com/news/reuters.com,2026:newsml_FWN44M0C1:0-openai-says-recently-banned-cluster-of-chatgpt-accounts-originating-in-russia-that-were-being-used-to-promote-the-international-burke-institute/"
  - "https://www.theregister.com/ai-and-ml/2026/08/25/slop-factory-bans-russians-for-using-slop-factory-to-create-slop/5292297"
---

## 概要

OpenAIは、ロシア発とみられる偽情報工作にChatGPTが悪用されていたとして、関連するアカウント群を特定し停止したと発表した。工作の中心にあったのは「International Burke Institute（IBI）」と称する架空のシンクタンクで、イスラエルに拠点を置くと偽って2025年2月に登録されていた。運営者はChatGPTにロシア語でプロンプトを与え、Substack、Telegram、X、Facebook、LinkedInなど複数のSNS向けに主に英語の投稿やコメントを生成させていた。OpenAIはロシアからの自社サービスへのアクセスを制限しているが、運営者はVPNを使ってこの制限を回避していたという。

## 手口と検出の経緯

IBIのウェブサイトには、フランシス・フクヤマやノーム・チョムスキーといった著名な学者の名を騙った記事が掲載されていたが、OpenAIが36本の関連記事を調査したところ、34本が他所からの盗用であり、一部は本来の専門分野と無関係な人物（オーストラリアの食品科学の教授に移民政策の論考を誤って帰属させるなど）に誤って紐付けられていたことが判明した。運営者はChatGPTに対し「文章から出自を示す特徴を取り除く」よう指示していたが、それでも英語表現の中にロシア語由来の直訳的な誤り(たとえば正しい英語表現の代わりにスラブ圏の交通信号になぞらえた「Svetofor coalition」という表現を使うなど)が残っており、これが人為的な痕跡として不自然さを露呈させる一因になったとみられる。工作にはロシアを好意的に描き、西側諸国やウクライナを批判する「主権指数(sovereignty index)」と呼ばれるコンテンツも含まれていた。

## 影響と今後の見通し

OpenAIによれば、実際に拡散した投稿の多くはエンゲージメントが低く、関連するTelegramチャンネルのフォロワー数も1チャンネルあたり1万〜2万人程度にとどまるなど、キャンペーンの直接的な到達範囲は限定的だったとされる。しかしOpenAIは、この事案の重要性は実際に到達した規模の大きさではなく、AIツールが偽の専門性や制度的な信頼性を作り出し、より大規模な工作のための「インフラ」を構築する能力を持つ点にあると強調している。生成AIが国家関与とみられる偽情報工作の効率化に利用される事例が相次いで表面化する中、AI企業側に求められる検知・対応体制の在り方が改めて問われている。
