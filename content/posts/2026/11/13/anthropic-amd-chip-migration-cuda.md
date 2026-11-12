---
date: "2026-11-13T08:07:05+09:00"
title: "Anthropic、独自AIでClaudeをAMD GPUに3日で移植、NvidiaのCUDA優位性低下を示唆"
description: "AnthropicはIPOロードショー資料で、自社AI「Mythos」がClaudeのAMD GPU移植を通常6〜12カ月かかる作業からわずか3日に短縮したと説明し、NvidiaのCUDAによる競争優位性が薄れつつあると主張した。"
tags:
  - AI
references:
  - "https://the-decoder.com/anthropic-says-ai-is-eroding-nvidias-cuda-lead-cutting-an-amd-chip-switch-from-months-to-three-days/"
  - "https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/"
---

## 概要

Anthropicは11月のIPOロードショー資料の中で、自社の内部モデル「Mythos」を使い、ClaudeをAMDのMI355X GPU上で動作させる移植作業を、通常であれば数十人のエンジニアが数カ月(6〜12カ月)を要する規模の仕事をわずか3日間で完了させたと明らかにした。Mythosはカーネルのほぼ100%をほとんど人手を介さずに書き直し・移植し、3日間のうちにMI355X上でほぼ100%の性能を達成したという。この事例は、AIによるコード移植の自動化がNvidiaのCUDAが長年築いてきた競争優位性を薄れさせつつあることを示す具体例として注目されている。

## マルチチップ戦略と「compute multipliers」

Anthropicは現在、AWS Trainium、Google TPU、Nvidia GPU、AMD GPUという4系統の主要チップファミリー全てでClaudeを訓練・運用している。共同創業者のTom Brownによれば、同社はこれらを単一の相互交換可能な計算プールとして扱い、ベンダーへの固定化を避けながら価格性能比に基づいて計算資源を配分しているという。各プラットフォームは専用のソフトウェアと推論スタックを必要とする高コストな取り組みだが、Anthropicは業界の懐疑的な見方にもかかわらず早期から複数チップ対応に賭け、これを数年かけて磨き上げてきた。

Brownはさらに、物理的な計算資源の必要量を減らす効率化要因である「compute multipliers(計算の乗数)」の発見も競争優位の一つだと強調した。例えば4倍の乗数があれば、同じモデルを4分の1の資源で訓練できる、あるいは既存のハードウェアでより高性能なモデルを生み出せる計算になる。こうした乗数は積み重なって複合的に効果を発揮し、Anthropicは今後Claude自身が再帰的な自己改善を通じて乗数を自力で発見できるようになることで、進歩がさらに加速すると見込んでいる。

## 出典と留意点

これらの数値や主張はAnthropicの投資家向けロードショー資料・動画(2026年11月)に基づくものであり、第三者による独立した検証は行われていない。Simon Willisonのブログ記事は、ロードショー動画をMacWhisperで文字起こしした上でまとめたものだと説明している。それでも、NvidiaのCUDAが長年築いてきたソフトウェア面での優位性に対し、AIによる自動移植が実用的な脅威となり得ることを示す初の具体的な事例として、業界内での反響を呼んでいる。
