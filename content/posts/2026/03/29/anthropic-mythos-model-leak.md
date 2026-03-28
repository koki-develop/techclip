---
date: "2026-03-29"
title: "Anthropicの未発表AIモデル「Claude Mythos」、CMS設定ミスによるデータ漏洩で存在が判明"
description: "AnthropicのCMSの設定ミスにより、開発中の次世代AIモデル「Claude Mythos」の内部文書が公開状態となり、同社史上最も強力なモデルの存在が明らかになった。"
tags:
  - AI
references:
  - "https://fortune.com/2026/03/26/anthropic-says-testing-mythos-powerful-new-ai-model-after-data-leak-reveals-its-existence-step-change-in-capabilities/"
  - "https://qz.com/anthropic-claude-mythos-data-leak"
  - "https://www.coindesk.com/markets/2026/03/27/anthropic-s-massive-claude-mythos-leak-reveals-a-new-ai-model-that-could-be-a-cybersecurity-nightmare"
---

## 漏洩の経緯と「Claude Mythos」の概要

Anthropicのコンテンツ管理システム（CMS）の設定ミスにより、未発表のAIモデル「Claude Mythos」（新ティア名「Capybara」）に関するドラフトブログ記事や内部文書が公開状態のデータキャッシュに漏洩した。約3,000件の未公開アセットがオンライン上で発見可能な状態となっていたという。このCMSではアップロードされたデジタルアセットがデフォルトで公開設定になっており、明示的に非公開に変更しない限り誰でもアクセス可能なURLが生成される仕組みだった。Fortuneが木曜夜にAnthropicに通知した後、同社はただちに公開アクセスを削除した。

Anthropicは今回の漏洩について「CMSの設定におけるヒューマンエラーにより、コンテンツの初期ドラフトがアクセス可能な状態になった」と認めた。同社の広報担当者は、「推論、コーディング、サイバーセキュリティにおいて意味のある進歩を遂げた汎用モデルを開発中」であり、「これまでに構築した中で最も能力の高いモデル」であると確認した。

## モデルの性能とサイバーセキュリティへの懸念

漏洩した内部文書によると、Claude MythosはAIの能力において「段階的な変化（step change）」をもたらすモデルと位置づけられている。具体的には、ソフトウェアコーディング、学術的推論、サイバーセキュリティのテストにおいて、現行のClaude Opus 4.6と比較して「劇的に高いスコア」を達成しているとされる。アーキテクチャ面では、Opusモデルよりもさらに大規模で高知能な新たなティアとして設計されているが、その分運用コストも高くなる見込みだ。

特に注目されるのはサイバーセキュリティ分野での能力で、Anthropicはこのモデルが「サイバー能力において他のどのAIモデルよりもはるかに先行している」と評価しており、大規模なサイバー攻撃を可能にするリスクがあることを認識している。そのため同社は、広範なリリースではなく、まずアーリーアクセスの顧客に限定した慎重な段階的公開を計画している。防御側のセキュリティコミュニティがAI駆動の脅威に対する準備を整える時間を確保することが狙いだ。今回の意図せぬ情報漏洩により、AIの安全性と段階的リリースの重要性が改めて浮き彫りとなった。
