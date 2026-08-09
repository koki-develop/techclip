---
date: "2026-08-10T02:08:33+09:00"
title: "Claude Codeの「auto mode」、8月14日からPro/Max/Teamでデフォルト化 危険操作の検出率は人間の6倍以上に"
description: "AnthropicはClaude Codeの権限確認代行機能「auto mode」を8月14日からPro・Max・Teamプランでデフォルト化すると発表した。"
tags:
  - AI
  - OSS
references:
  - "https://www.itmedia.co.jp/aiplus/article/2608/09/2000000465/"
  - "https://9to5mac.com/2026/08/07/psa-claude-code-enabling-auto-mode-as-default-next-week-anthropic-says/"
  - "https://thenewstack.io/claude-code-auto-mode/"
---

## 概要

Anthropicは8月7日(米国時間)、AIコーディングツール「Claude Code」の「auto mode」を8月14日からPro・Max・Teamプランでデフォルト化すると発表した。auto modeは、コマンド実行のたびに人間へ許可を求める従来のフローに代わり、専用の分類器が1件ずつコマンドを評価し、取り消し不能な操作や破壊的な操作、作業環境の外に影響を及ぼす操作を自動的にブロックする仕組み。ブロックされた場合、Claudeは安全な代替手段を提案するか、改めて人間に確認を求める。同一セッション内で3回連続、あるいは合計20回ブロックが発生すると、手動承認モードへ自動的に切り替わる安全弁も備えている。

## 検出精度と安全性の検証結果

Anthropicが1,053人の有料テスターを対象に行った対照実験によれば、人間による危険なコマンドの検出率は約13.6%にとどまったのに対し、auto modeは89%を検出したという。さらに、人間の検出精度はセッションが50プロンプトを超えるあたりから約5%まで低下する傾向が見られた一方、auto modeの検出精度はセッションの長さによらず横ばいを維持したとしている。レッドチーミングによる継続的な改善では、危険な操作の見逃し率を12%から7%まで引き下げ、720回の攻撃的な試行に対してはゼロ件の突破を記録したという。ただしAnthropicは「分類器がリスクを完全になくすことはできない」とし、本番環境への変更には引き続き人間によるレビューを推奨している。

## 対象範囲と料金、今後の展開

今回デフォルト化されるのはPro・Max・Teamプランで、ユーザーや管理者が別の設定を選択していない限り自動的に有効になる。Enterpriseプラン、Claude API、AWS・Google Cloud・Microsoft Foundry経由の利用については1カ月以内にデフォルト化される予定だという。またAnthropicは、auto modeの分類器処理に伴う追加トークン分については課金しない方針も明らかにした。TeamおよびEnterprise顧客のデータでは、auto mode利用時にプルリクエストの提出数が約25%増加しており、生産性向上の効果も示唆されている。今回の変更は、ルーティン機能や音声モード、Mac向けアプリ内ブラウザなど、Claude Codeで最近追加された一連の機能強化の流れに位置づけられる。
