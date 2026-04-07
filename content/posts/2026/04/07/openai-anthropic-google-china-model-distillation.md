---
date: "2026-04-07T10:38:41+09:00"
title: "OpenAI・Anthropic・Google、Frontier Model Forumを通じて中国によるモデル蒸留攻撃への共同対策を発表"
description: "OpenAI、Anthropic、Googleの3社がFrontier Model Forumで連携し、中国AI企業による無断モデル蒸留（Adversarial Distillation）の検知・阻止に向けた脅威情報の共有を開始した。"
tags:
  - AI
references:
  - "https://www.bloomberg.com/news/articles/2026-04-06/openai-anthropic-google-unite-to-combat-model-copying-in-china"
  - "https://www.frontiermodelforum.org/issue-briefs/issue-brief-adversarial-distillation/"
  - "https://www.cnbc.com/2026/02/24/anthropic-openai-china-firms-distillation-deepseek.html"
---

## 概要

OpenAI、Anthropic、Googleの3社は2026年4月、Frontier Model Forum（FMF）を通じた共同対策として、中国AI企業による無断モデル蒸留攻撃（Adversarial Distillation）の検知・阻止に向けた脅威情報の相互共有を開始したと発表した。FMFはOpenAI、Anthropic、Google、Microsoftが2023年に設立した業界非営利組織で、今回の協調行動はフロンティアAIモデルの知的財産保護を目的とした初の本格的な共同取り組みとなる。

背景には、2026年2月に相次いで明らかになった「産業規模」の蒸留攻撃キャンペーンがある。Anthropicは、DeepSeek・Moonshot AI・MiniMaxの3社が合計約2万4千の不正アカウントを使って約1600万件ものClaudeとのやり取りを生成し、モデルの応答データを収集していたと公表。OpenAIも同時期、米下院中国特別委員会への提出文書の中でDeepSeekによる蒸留活動の継続的な観測を報告した。

## 攻撃手法と規模

Adversarial Distillationとは、大規模な「教師モデル」の出力データを使って小型の「生徒モデル」を訓練することで、研究コストをかけずにモデル能力を模倣する技法である。正規の用途も存在するが、利用規約への同意なしに組織的・大規模に行われる場合は知的財産の侵害とみなされる。

Anthropicが特定した攻撃の内訳は以下の通りだ。DeepSeekは15万件超のやり取りを通じて推論能力や政治的に敏感な質問への応答パターンを収集し、Moonshot AIは約340万件のクエリでエージェント推論・ツール使用・コーディング・コンピュータビジョンを標的にした。MiniMaxは最大規模の約1300万件の交換を実施し、コーディングとツール活用能力の吸い出しを図った。攻撃者たちは商業プロキシサービスと「ヒドラクラスター」と呼ばれる2万以上の不正アカウント群を組み合わせ、検知を回避するために蒸留トラフィックを無関係なリクエストに紛れ込ませる手口を使っていた。

## FMFの対応と分類フレームワーク

FMFは2026年2月16日に脅威情報共有の進捗レポート、同23日には「Adversarial Distillation」のイシューブリーフを公表し、攻撃手法を次の5種類に分類した：Chain-of-Thought Exfiltration（思考過程の抽出）、Chain-of-Thought Critiquing（批評プロセスの模倣）、Chain-of-Thought Autograding（自動採点機能の複製）、Prompt Generation for Reinforcement Learning（強化学習用プロンプト生成）、Synthetic Data Generation（合成データ生成）。数学・科学的推論、コーディング、マルチモーダル処理といった高付加価値能力の選択的な抽出は、フロンティアモデルに組み込まれた安全機能を迂回できるとして特に危険視されている。

## 安全保障上の懸念と反論

Anthropicは「蒸留されたモデルは必要なセーフガードを欠く」として、権威主義的政府によるサイバー攻撃・監視・偽情報工作への転用リスクを強調。OpenAIもDeepSeekのモデルが危険な用途における「意味のあるガードレールを持たない」と批判した。一方でGoogleは「一般ユーザーのデータや可用性への直接リスクはない」との立場を示し、RANDやカウンターポイント・リサーチなどの分析機関は、蒸留が業界標準の技法であり、今回の発表のタイミングと文脈が中国企業の半導体アクセス制限という地政学的文脈と重なると指摘している。米中AI覇権競争が激化するなか、今後もAI知的財産の保護を巡る議論は続くと見られる。
