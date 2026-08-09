---
date: "2026-08-10T02:08:33+09:00"
title: "Spring生みの親Rod Johnson氏らが手掛けるJVM向けAIエージェントフレームワーク「Embabel」が1.0に到達"
description: "Spring Frameworkの生みの親Rod Johnson氏らが開発するJVM向けAIエージェントフレームワーク「Embabel」が正式に1.0へ到達し、GOAPによる動的なタスク計画が特徴として紹介された。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://www.infoq.com/news/2026/08/embabel-1/"
---

## 概要

Spring Frameworkの生みの親として知られるRod Johnson氏らが開発するJVM向けAIエージェントフレームワーク「Embabel」が、正式に1.0のGeneral Availabilityに到達した。JavaやKotlinの開発者が、プロンプトやツール呼び出しを手作業でオーケストレーションするのではなく、エージェントをゴール・アクション・両者をつなぐ条件から成る型付きドメインオブジェクトとして定義できる点が最大の特徴だ。Johnson氏自身もSNSでリリースを発表し、大きな反響を呼んでいる。

## GOAPによる動的な計画

Embabelを他のエージェントフレームワークと区別する中心的な仕組みが、ビデオゲームAIに由来する概念「Goal-Oriented Action Planning(GOAP)」の採用だ。あらかじめ決められたスクリプトに従うのではなく、エージェントは前提条件と効果が定義された利用可能なアクション群を与えられ、プランナーが実行時にゴールを満たすアクションの並びを探索する。途中で状況が変化した場合もプランナーが再評価を行い、開発者があらゆる分岐をあらかじめ想定しておかなくても代替の経路を見つけられるという。

## Spring AIとの関係とモデルの柔軟性

Embabelは、Springチームが提供するモデル呼び出し・ツール呼び出しライブラリ「Spring AI」の上に構築されている。公式アナウンスでは「Spring AIがServlet APIの水準に位置するのに対し、EmbabelはSpring MVCのような存在だ」と説明されており、開発者は実装の詳細を自前でパースするのではなく、ゴールとアクションを宣言的に記述できる。またモデル面では、OpenAI、Anthropic、Gemini、Bedrock、Mistral、DeepSeekや自前ホスティングのモデルをサポートし、個々のアクションを特定のモデルにルーティングしたり、コストや性能に応じたロールベースのエイリアスを使い分けたりできる。

## 他フレームワークとの比較と今後

記事では、あらかじめノードとエッジを定義するグラフ指向の「LangGraph」、アクターモデルによるインフラと耐障害性を重視する「Akka Agentic Platform」、Kotlinの言語機能を活かしたJetBrainsの「Koog」といった競合との違いにも触れられている。Embabelは実行時にプランを組み立てる点でこれらと一線を画す。Spring Bootを使うチームにとって、今回の1.0リリースは「様子見」から「実際に評価してみる」段階への転換点であるとされている。
