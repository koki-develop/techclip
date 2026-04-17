---
date: "2026-04-17T10:38:05+09:00"
title: "OpenAI、生命科学特化AIモデル「GPT-Rosalind」を発表——創薬・ゲノミクス研究を加速"
description: "OpenAIが生命科学研究に特化したAIモデル「GPT-Rosalind」を発表し、Amgen・Moderna・Allen Instituteなど向けに研究プレビューとして提供を開始した。"
tags:
  - AI
references:
  - "https://openai.com/index/introducing-gpt-rosalind/"
  - "https://venturebeat.com/technology/openai-debuts-gpt-rosalind-a-new-limited-access-model-for-life-sciences-and-broader-codex-plugin-on-github"
  - "https://www.axios.com/2026/04/16/openai-models-life-sciences-drugs"
---

## 概要

OpenAIは2026年4月16日、生命科学研究に特化したAIモデル「GPT-Rosalind」を発表した。モデル名はDNAの二重らせん構造の解明に貢献した20世紀の英国人化学者ロザリンド・フランクリンにちなんで命名されている。GPT-Rosalindは生化学・ゲノミクス・タンパク質工学・創薬・トランスレーショナルメディシンといった分野に最適化されており、OpenAIにとって初めての生命科学専用モデルとなる。現在は米国の認定エンタープライズ顧客向けに研究プレビューとして提供が開始されており、Amgen・Moderna・Allen Institute・Thermo Fisher Scientificなどの大手製薬・バイオテク企業や研究機関が初期ユーザーとして参加している。

## 主な機能と研究支援能力

GPT-Rosalindは、科学者が従来数年単位の専門的な知識の統合を要していた作業を支援することを目的としている。具体的には、文献エビデンスの統合（Evidence Synthesis）、生物学的仮説の生成、実験計画の立案、マルチステップの研究タスクを実行できる。さらに科学データベースへのクエリ、最新の学術論文の参照、新規実験の提案といった機能も備えており、研究の初期フェーズを大幅に加速することが期待されている。

モデルへのアクセスはChatGPT・Codex・APIを通じて提供され、Codex向けには50以上の科学ツールおよびデータソースと連携する「Life Sciences研究プラグイン」がGitHub上で無償公開されている。このプラグインにより、研究者は既存のツール群をそのまま活用しながらGPT-Rosalindの能力を組み合わせることができる。

## ベンチマーク性能

GPT-Rosalindは文献取得やプロトコル設計などの研究タスクを評価するベンチマーク「LABBench2」において、GPT-5.4を11タスク中6タスクで上回る性能を示した。Dyno Therapeuticsとの共同評価では、予測タスクにおいて10回の提出のうち最良の結果が人間の専門家の95パーセンタイルを上回り、配列生成タスクでも84パーセンタイルに達した。

## エコシステムとセキュリティ

OpenAIはGPT-Rosalindを広範なオープンソースリリースではなく「Trusted Access」プログラムの形で限定展開し、エンタープライズグレードのセキュリティコントロールとアクセス管理を提供している。これにより、厳しい規制環境下に置かれる製薬企業や研究機関が求めるデータガバナンス要件を満たすとしている。GPT-Rosalindはモデル単体の提供にとどまらず、科学者が日常的に使用するツールとシームレスに統合できるエコシステムの構築を目指しており、Google DeepMindなどが推進する生命科学AI分野での競争が一層激化している。
