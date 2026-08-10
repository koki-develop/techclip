---
date: "2026-08-11T08:09:52+09:00"
title: "OpenAI、ガードレールを解除した「GPT-5.6-Cyber」を発表 認可防御担当者向けにサイバー脆弱性の先行発見を支援"
description: "OpenAIがサイバーセキュリティ支援プログラム「Daybreak」を拡張し、システムレベルのガードレールを外した専用モデル「GPT-5.6-Cyber」と、Red/Blue両チーム向けのアクセス階層を新設した。"
tags:
  - AI
  - Security
references:
  - "https://the-decoder.com/openai-launches-gpt-5-6-cyber-to-help-defenders-find-vulnerabilities-before-attackers-do/"
  - "https://www.cnbc.com/2026/08/10/open-ai-daybreak-cybersecurity.html"
  - "https://www.neowin.net/news/openai-launches-gpt-56-cyber-and-expands-daybreak-with-red-and-blue-access-tiers/"
---

## 概要

OpenAIは8月10日、サイバーセキュリティ支援プログラム「Daybreak」を拡張し、認可された防御担当者向けにシステムレベルのガードレールを解除した新モデル「GPT-5.6-Cyber」を発表した。攻撃者がAIを駆使した攻撃を仕掛ける前に、防御側が脆弱性を先んじて発見・検証できるよう支援することが狙いだ。Daybreakは今回、マルウェア分析や脆弱性検出などの防御的タスクに対応する「Daybreak Blue」と、脆弱性研究や侵入テストなど攻撃的セキュリティ研究に対応する「Daybreak Red」の2階層に再編された。アクセスには身分確認と法的宣言が必要とされ、2026年9月からは全アカウントでハードウェアセキュリティキーの利用が必須となる。

## 技術的な詳細

OpenAIの内部ベンチマーク「Advanced Cybersecurity Completion Rate」によると、GPT-5.6-Cyberは機密性の高いサイバーセキュリティ関連の質問の95%に回答できるとされる。これは、標準版のGPT-5.6 Solがほぼすべてをブロックしてしまうような複雑なセキュリティ関連の問い合わせにも対応できることを意味する。実際の成果として、GPT-5.6-CyberはChromeのV8エンジンに存在していた未発見の脆弱性2件を特定しており、これらはCVE-2026-15903として登録された。

OpenAIの「Preparedness Framework」によるリスク評価では、GPT-5.6-Cyberのサイバー能力は「High」レベルに位置づけられており、最上位の「Critical」には至っていない。ただし、次世代モデルとされる「Astra」がCriticalレベルに達する可能性が指摘されており、AIのサイバーセキュリティ関連能力が急速に進化していることがうかがえる。ガードレールを解除した強力なモデルを一般提供するにあたり、Red/Blueのアクセス階層化や身分確認、ハードウェアセキュリティキーの必須化といった多重の認可プロセスは、攻撃側への悪用リスクを抑えつつ防御側の能力向上を図るOpenAIの姿勢を反映している。

## 今後の展望

AIによる自動化されたサイバー攻撃・防御の能力が急速に高度化する中、OpenAIは今回の拡張を「攻撃者に先んじる」ための取り組みと位置づけている。次世代モデルでリスク評価がCriticalレベルに達する可能性が示唆されていることから、今後は認可プロセスや監視体制のさらなる強化が求められる可能性がある。
