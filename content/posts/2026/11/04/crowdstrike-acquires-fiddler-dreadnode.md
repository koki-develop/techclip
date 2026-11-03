---
date: "2026-11-04T08:07:08+09:00"
title: "CrowdStrike、AIエージェントの「飛行記録装置」と「攻撃者視点」を4.95億ドルで獲得"
description: "CrowdStrikeがAI観測性のFiddler AIとAI攻撃テストのDreadnodeを合計4.95億ドルで買収し、AIエージェントの監視・防御を強化する。"
tags:
  - Security
  - AI
  - Other
references:
  - "https://www.gurufocus.com/news/9164784/crowdstrike-crwd-to-acquire-ai-security-firms-fiddler-ai-and-dreadnode-for-495m"
  - "https://cyberscoop.com/crowdstrike-acquires-fiddler-dreadnode-ai-security/"
  - "https://www.securityweek.com/crowdstrike-reportedly-paying-495-million-for-ai-security-firms-fiddler-dreadnode/"
---

## 概要

サイバーセキュリティ大手のCrowdStrikeは11月3日、バルセロナで開催中の「Fal.Con Europe」において、AIセキュリティ企業2社を合計4.95億ドルで買収する契約を結んだと発表した。The Wall Street Journalの報道によれば、AIエージェントの可観測性を手がけるFiddler AIを約4億ドル、AIモデルへの攻撃テストを行うDreadnodeを約9500万ドルで取得する。CrowdStrikeは価格を公式には開示していないが、支払いは現金を主体としつつ、一部を業績条件付きのベスティング株式で行う構成になっているという。買収完了は2027会計年度第4四半期(2027年1月31日期)を見込む。

## 2社の技術とCrowdStrikeの統合戦略

Fiddler AI(2018年創業、拠点はパロアルト)は、デプロイ後のAIエージェントの挙動を評価し、意思決定プロセスを追跡し、行動の「ドリフト」やハルシネーションを検出する観測性プラットフォームを開発してきた。LangGraph、Amazon Bedrock、Google ADKといった主要フレームワークとの連携にも対応している。同社は今年1月にシリーズCで3000万ドルを調達し、累計調達額は1億ドルに達していた。CrowdStrikeはFiddlerの技術を「Falcon Observe」として自社プラットフォームに統合し、デプロイ前のエージェント評価や推論の追跡、異常な振る舞いの検知に用いる計画だ。CEOのGeorge Kurtz氏はFiddlerを「すべてのエージェントのための飛行記録装置(フライトレコーダー)」と表現し、規制当局や取締役会からエージェントの行動説明を求められた際の説明責任を果たす手段になると強調した。

一方のDreadnode(2023年創業)は、ユーザーが平易な言葉でテスト内容を記述するだけで、ジェイルブレイクやプロンプトインジェクションを含む100種類以上の既知の攻撃手法を自動実行し、OWASP Top 10 LLMやNIST AI Risk Management Frameworkに脆弱性をマッピングする、デプロイ前のAIセキュリティテスト基盤を提供している。2025年初めにシリーズAで1400万ドルを調達していた。Dreadnodeの検出結果は、CrowdStrikeの異常検知・対応製品「Falcon Guardian」にポリシー推奨として取り込まれる予定で、同CEOのBrad Palm氏は「システムの欠陥を見つけるのに最も適しているのは攻撃者だ」という自社の設計思想を語っている。

## 背景と今後の見通し

CrowdStrikeがこの買収で解決を目指すのは、AIエージェントが正当な認証情報や承認済みのツールを悪用しなくても、判断を誤ったり指示を無視したりしうるという課題だ。従来のセキュリティテストはネットワークやアクセス権限の検証を主眼としており、モデル層の推論やエージェントの行動パターンそのものを評価する手段を欠いていた。FiddlerとDreadnodeの組み合わせは、デプロイ前の攻撃耐性テストとデプロイ後の継続的な行動監視という両面からこの穴を埋めるものとなる。両製品は2027会計年度第4四半期に一般提供を開始する予定で、同時に発表された「AI Kill Switch」機能は、Falcon Guardian上で管理者が誤動作するAIエージェントを停止し、ネットワークアクセスを遮断できるようにするものだ。急速に拡大するAIエージェントの企業導入に対し、セキュリティ企業各社がこの分野への投資を加速させている状況の中、CrowdStrikeは今回の買収でAIエージェント特有のリスクに対応する製品群を一気に整備した格好だ。
