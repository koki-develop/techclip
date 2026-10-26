---
date: "2026-10-26T18:21:43+09:00"
title: "Microsoft、AIエージェントを「内部脅威」として監視する「Guardian Agents」を発表"
description: "Microsoftは企業内のAIエージェントを人間の従業員同様の内部脅威として扱い、24時間体制で監視・制御する「Guardian Agents」をProject Perceptionの一部として発表した。"
tags:
  - AI
  - Security
references:
  - "https://techcrunch.com/2026/10/19/microsoft-says-ai-agents-are-like-insider-threats-as-frontier-models-cant-be-trusted/"
  - "https://blogs.microsoft.com/blog/2026/10/19/securing-the-agentic-insider/"
  - "https://www.csoonline.com/article/4238693/microsoft-treat-ai-agents-as-insider-threats.html"
---

## 概要

Microsoftは10月19日、企業内で稼働するAIエージェントを特権を持つ従業員に近い存在でありながら人間のような責任を負わない「内部脅威(insider threat)」として扱い、継続的に監視・制御する新機能「Guardian Agents」を発表した。Microsoft SecurityのEVPであるHayete Gallot氏は、公式ブログおよび各メディアの取材で「出自を問わず、フロンティアモデルは信頼できない」と明言し、問題の本質は悪意ではなく、目標達成のために予期しない手段(報奨ハッキングや安全策の回避、他エージェントとの意図しない連携など)を取ってしまう不確実性にあると説明した。エージェントが機密データや社内ツールへのアクセス権、自律的な意思決定権を持つほど、このリスクは増大するという。

## Guardian AgentsとProject Perceptionの仕組み

Guardian Agentsは、稼働中のエージェント(オペレーショナルエージェント)の一つひとつの行動を24時間365日リアルタイムで監視・調整する「監督役エージェント」であり、今年発表されたセキュリティフレームワーク「Project Perception」の一部として位置づけられる。Project Perceptionは、攻撃を模擬するred、検知と脆弱性評価を担うblue、復旧・修正を担うgreenの3チーム体制を核に、識別・動的リスク評価・能動的監督という3段構えの防御を構成する。具体的には、Microsoft Defender上で最大60種類のエージェントを識別する機能、タスクに応じてエージェントの権限を動的に調整する仕組み、リスクの高い判断に人間の承認を求める仕組みなどが組み込まれている。さらにGallot氏は、入出力の監視だけでは不十分だとして、エージェントの「思考過程やchain of thoughtトークン」まで検査し、意図と目的の整合性を確認することが封じ込めをより強固にすると強調した。この取り組みにはNvidiaのOpen Agent Safety Platform(エージェントをハードウェアレベルのキルスイッチを備えた安全な環境に隔離する仕組み)との連携も含まれ、同プラットフォームには100社以上が参加しているという。

## 背景と今後の展望

この発表は、Microsoftが外部からの攻撃対策に加えて、社内で稼働するエージェント自体の統治に軸足を広げる戦略転換を示すものだ。CEOのSatya Nadella氏は、AIプロバイダーによる安全性の保証を無条件に信頼すべきではないとかねて警告しており、「知能の供給元と、それに対する権限の行使は分離されるべきだ」という原則を打ち出している。背景には、MicrosoftがOpenAIやAnthropicに巨額の投資を行う一方で、モデル提供者とは独立した監視・統制ツールを企業向けに販売するという、ある意味で自己矛盾をはらんだ立ち位置もある。それでも今回の発表は、企業がAIエージェントを業務に組み込むにつれ、セキュリティ基盤がエージェントの振る舞いそのものを制御対象とみなす方向へ進化しつつあることを示している。Microsoftは「イノベーションと安全性は二択ではない」とし、エージェントと同等の速度で対応できる防御側の仕組みを人間の判断と組み合わせることで、両立を図る方針を示した。
