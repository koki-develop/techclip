---
date: "2026-09-20T18:12:30+09:00"
title: "SalesforceがNvidia基盤の企業向け推論モデル「Koa」発表、Anthropicとの新提携「Claudeforce」も始動"
description: "SalesforceがNvidiaのNemotron 3 Superを追加学習したCRM特化の推論モデル「Koa」を発表し、Anthropicとの新パートナーシップ「Claudeforce」も同時に始動した。"
tags:
  - AI
references:
  - "https://techcrunch.com/2026/09/15/salesforce-and-nvidias-new-reasoning-model-is-everything-the-ai-labs-should-fear/"
  - "https://www.constellationr.com/insights/news/salesforce-launches-koa-crm-reasoning-model-built-nvidias-nemotron"
  - "https://blogs.nvidia.com/blog/jensen-huang-dreamforce/"
---

## 概要

Salesforceは年次イベント「Dreamforce」で、Nvidiaのオープンウェイトモデル「Nemotron 3 Super」をベースに独自の合成データで追加学習した企業向け推論モデル「Koa」を発表した。Salesforceが構築した評価指標「CRM Bench」では、主要なフロンティアモデルと同等以上の性能を、エラー率3分の1という水準で達成したとしている。同時にAnthropicとの新たなパートナーシップ「Claudeforce」も発表され、営業・マーケティング・カスタマーサポート領域でのAIエージェント活用を両輪で加速させる構えだ。

## 技術的な詳細

Koaの最大の特徴は、実際の顧客データを一切使わずに学習された点にある。SalesforceのAI担当EVPであるJayesh Govindarajan氏によれば、同社は「顧客対応担当者のペルソナを設定した顧客サービス環境をシミュレートした」といい、製造・金融・ヘルスケア・旅行など14以上の業界にまたがる合成シナリオを構築。各シナリオにはペルソナ、アクションの順序、必要なツール呼び出しが組み込まれている。学習には27年分にわたるSalesforce独自のCRM知見が反映されており、NvidiaのNeMo RL、NeMo Gym、NeMo AutoModelを用いた教師あり微調整と強化学習による事後学習を、Salesforceの「信頼の境界」内で実施した。Govindarajan氏は「推論についてはこれまでフロンティアモデルの提供元に頼ってきたが、それも今までの話だ」と述べ、自社インフラ内でモデルの重みを制御できる体制への転換を強調している。Nemotronを基盤に選んだ理由として、米国内で開発された透明性の高いオープンモデルであること、最先端の性能を持つこと、データの出所が明確であることの3点を挙げた。

## パイロット展開とロードマップ

Koaはすでに1-800Accountant、Baxter Credit Union、Engine、Formula 1、UChicago Medicine、Xeroなど複数企業でパイロット導入が進んでおり、リード獲得の見極め、営業機会の適格化、サービスケースの解決といった実務のCRM業務を主な対象としている。10月にはMissionforce向けのNemotronベースモデルが展開されるほか、パイロット規模の拡大も見込まれており、Agentforceでの一般提供は2026年下半期に米国から開始される予定だ。

## Anthropicとの提携「Claudeforce」の位置付け

NvidiaのCEOであるJensen Huang氏はDreamforceの基調講演で、AIがインフラストラクチャ層になれば「あらゆることを知り、あらゆることができるようになる」と述べ、安全性についても「エンジニアリング上の課題であり、革新と両立できる」と強調した。もっとも今回の発表でNvidia側がAnthropicとの関係に直接言及した形跡はなく、Claudeforceはあくまでもう一方のパートナーであるSalesforceが主導する枠組みと位置付けられる。TechCrunchが指摘するように、SalesforceはKoaのような特化型モデルをコスト・トークン効率・データ保護の観点で使い分けつつ、複雑なタスクではClaudeなどのフロンティアモデルへのルーティングも継続する方針とみられ、自社開発モデルとフロンティアモデル提供元との提携を並存させるハイブリッド戦略を志向していることがうかがえる。
