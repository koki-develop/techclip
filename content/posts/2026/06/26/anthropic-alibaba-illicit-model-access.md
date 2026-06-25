---
date: "2026-06-26T02:50:13+09:00"
title: "AnthropicがAlibabaによる過去最大のClaude蒸留攻撃を告発——2,880万回の不正アクセス、米政府に規制強化を要請"
description: "AnthropicはAlibabaとそのAI部門Qwenが約25,000の偽装アカウントで2,880万回ものClaudeへの不正アクセスを行い、ソフトウェアエンジニアリングや自律推論の能力を違法に抽出したと告発し、米政府に規制強化を訴えた。"
tags:
  - AI
  - Security
references:
  - "https://www.bloomberg.com/news/articles/2026-06-24/anthropic-accuses-alibaba-of-illicitly-accessing-its-ai-models"
  - "https://www.cnbc.com/2026/06/24/anthropic-alibaba-distillation-campaign.html"
  - "https://www.japantimes.co.jp/business/2026/06/25/companies/anthropic-alibaba-illegal-access/"
  - "https://cybersecuritynews.com/anthropic-accuses-alibaba/"
  - "https://americanbazaaronline.com/2026/06/25/anthropic-accuses-alibaba-of-massive-ai-distillation-attack-483523/"
---

## 概要

Anthropicは2026年6月24日、中国テック大手Alibabaとその傘下のAI研究部門Qwenが、「過去最大規模の蒸留攻撃（distillation attack）」をClaudeモデルに対して実施したと告発した。Anthropicは米上院議員らへの書簡およびホワイトハウス当局者への報告を通じてこの事実を明らかにし、米国のAI優位性を守るための規制強化を強く求めた。攻撃は2026年4月22日から6月5日にかけて行われ、約25,000の偽装アカウントを用いたClaudeとの交換回数は2,880万回以上に達した。

## 攻撃手法：「敵対的蒸留」とは

今回の攻撃で使われた「敵対的蒸留（adversarial distillation）」は、高性能なAIモデルに大量のプロンプトを送り、その回答パターンや推論構造を収集することで、自社の低性能モデルを改善・強化する手法だ。通常、蒸留は自社システム内で合法的に行われるが、本件では他社のモデルに許可なくアクセスして知的財産を抽出している点が問題とされている。Anthropicは書簡の中で「これらの攻撃は違法かつ組織的に、産業規模で実施されている」と断言し、AlibabaがR&D投資を回避しながら最先端の能力を獲得しようとしていると批判した。

## 標的とされた機能と安全上のリスク

攻撃が集中したのは、Anthropicの最新モデル「Mythos Preview」が持つ高度な機能群、特にソフトウェアエンジニアリングと自律的な推論（agentic reasoning）の領域だ。これらはAnthropicの競争優位の根幹をなすと同時に、商業的価値の高い機能でもある。AnthropicはさらにIPの窃取にとどまらないリスクも指摘している。敵対的蒸留によって開発されたモデルは「安全ガードレールを欠くことが多い」とし、こうしたモデルの普及が安全保障上の脅威につながりうると警告した。

## 政府への働きかけと米中AI競争の文脈

Anthropicはホワイトハウスや米上院議員に詳細を報告し、規制強化を求めた。これを受け、上院のBill HagertyとAndy Kimは国防関連法案の修正案として、米国のAIモデル出力を不正利用した中国企業を「ブラックリストへの登録や制裁対象とする」条項の追加を提案している。米当局者は、こうした不正蒸留による損害はシリコンバレー各社に数十億ドル規模の損失をもたらしていると推計している。

今回の告発は突発的な事件ではない。Anthropicは2026年2月にもDeepSeek、Moonshot、MiniMaxの3社による「産業規模の蒸留キャンペーン」を確認・公表しており、その後も攻撃の規模と巧妙さが増していると述べていた。今回のAlibabaによる攻撃は、それをさらに上回る過去最大の事例として記録された。AIの知的財産保護と米中間の技術覇権争いが交錯するこの問題は、今後の規制の在り方に大きな影響を与えることが予想される。
