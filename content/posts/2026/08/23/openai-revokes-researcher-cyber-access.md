---
date: "2026-08-23T08:02:24+09:00"
title: "OpenAIのサイバー研究プログラム、検証済み研究者のアクセスが予告なく停止"
description: "OpenAIのセキュリティ研究者向け限定プログラム「Trusted Access for Cyber」で、米欧圏外の研究者らのアクセスが予告なく停止され、OpenAIは自社側の技術的問題と説明している。"
tags:
  - AI
  - Security
references:
  - "https://techcrunch.com/2026/08/19/researchers-complain-that-openai-revoked-their-access-to-limited-cyber-program/"
---

## 概要

複数のセキュリティ研究者が、OpenAIが提供するサイバーセキュリティ研究向けの限定プログラムへのアクセスを、予告なく突然剥奪されたと訴えている。TechCrunchが取材した5名の研究者はいずれも米国およびヨーロッパ以外に居住しており、2026年8月19日、ChatGPTのCyberページ上で「identity could not be verified(本人確認ができませんでした)」というメッセージが表示され、アクセスできなくなったという。OpenAIはこれについて「一部の利用者に影響する技術的な問題(technical issue affecting a limited number of users)」だったと認め、該当ユーザーに再検証を求めている。

## プログラムの内容

問題となっているのは「Trusted Access for Cyber(TAC)」と呼ばれるプログラムで、本人確認を経た検証済みの研究者に対し、通常より制限を緩和した(guardrailsを削減した)強力なAIモデルへのアクセスを提供するものだ。目的は脆弱性の発見とバグ報告であり、セキュリティコミュニティとOpenAIの協業の枠組みとして位置づけられている。OpenAIは2026年8月10日、このプログラム内に新たな階層を導入しており、防御的なセキュリティ業務向けにカスタマイズされた保護機能を備える「Daybreak Blue」(GPT-5.6 Solを含む)と、脆弱性研究およびエクスプロイト検証に特化した「Daybreak Red」の2種類が用意されている。

## 研究者らの反応と背景

OpenAIは今回の件を「こちら側の問題(This was an issue on our end)」だとし、ユーザー体験が目標水準に達していなかったことを認めているが、研究者らはより根本的な不満も口にしている。ガードレールが正当な研究活動の妨げになっている(guardrails prevent legitimate work)という批判は以前から続いており、今回のアクセス停止はその不満を再燃させる形となった。なお、競合のAnthropicも同様の枠組みとして「Cyber Verification Program」を提供しており、AI企業各社がセキュリティ研究者との協業モデルを模索する中で、検証プロセスの透明性や安定運用が課題として浮かび上がっている。
