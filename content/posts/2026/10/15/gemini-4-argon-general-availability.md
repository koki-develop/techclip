---
date: "2026-10-15T18:14:00+09:00"
title: "Google「Gemini 4 Argon」一般公開、期間限定の低価格APIとAntigravity連携で攻勢"
description: "GoogleがフラッグシップモデルGemini 4 ArgonをGemini app・API・Antigravityなど全チャネルで一般公開し、2026年11月30日までの期間限定低価格APIを提供する。"
tags:
  - AI
references:
  - "https://blog.google/innovation-and-ai/products/gemini-app/gemini-4-argon-availability/"
  - "https://venturebeat.com/technology/google-makes-gemini-4-argon-broadly-available-with-limited-time-low-api-pricing-of-2-10-per-1m-token"
  - "https://9to5google.com/2026/10/13/gemini-app-4-argon/"
---

## 概要

Googleは10月13日、フラッグシップモデル「Gemini 4 Argon」を一般公開した。これまでサイバーセキュリティ防御者向けのFairwind Programや、月額99.99ドル以上のAI Ultraサブスクライバーに限定提供されていたが、今回Gemini app、Gemini API、Google AI Studio、Antigravity開発環境、Gemini Enterprise、AI Mode in Searchなど主要チャネルすべてに展開され、AI Pro層にも開放された。Gemini appのモデル選択メニューには3.5 Flash-Lite、3.8 Flash、3.1 Pro、4 Argonが並び、APIでは2026年11月30日まで入力$2・出力$10(100万トークンあたり)という期間限定の低価格が設定されている。12月1日以降は入力$4・出力$20の通常価格に移行する。

## 性能とベンチマーク

Argonは推論能力の強化を前面に押し出し、ソフトウェア開発・財務分析・法務・サイバーセキュリティ・科学研究など専門領域のワークフローに対応するマルチモーダルモデルとして位置づけられている。特殊なAPIプロトコルを使えば入出力合計で最大100万トークンの拡張推論予算を扱える。Vals AI Indexでは68.90%で首位となり、Claude Sonnet 5.5の67.04%を上回った一方、Artificial Analysis Intelligence Indexでは53でGPT-6 AstraやClaude Fable 5.1と同水準にとどまり、Opus 5.5やSonnet 5.5には及ばなかった。Googleが公開した個別ベンチマークでは、DeepSWE v1.1で77.9%、Embodied Reasoning QAで87%、AutomationBenchで51.3%、Legal Agent Benchmarkで19.6%を記録している。セキュリティ面ではGray Swanの間接プロンプトインジェクション攻撃成功率0.7%、コーディング評価での不正なショートカット試行2%という結果も示された。Red Dragon AIのSam Witteveenは「非常に良いモデルだが、最良のモデルかと言われるとそうは思わない」と評し、視覚理解やコード生成、クリエイティブメディア生成の強さを認めつつ、競合の開発環境面には留保をつけた。

## コーディングとエージェント機能

応答品質では、より直接的で曖昧な言い回しを避けた回答や、繰り返し・決まり文句の削減、長時間タスクでの進捗表示の改善が図られた。コーディング面では大幅な強化が加えられ、macOS版Gemini appではチャットとタスクモードをメイン画面から切り替えられるようになり、Google Antigravityのエージェント型コーディングインターフェースに直接アクセスできる。タスクモードではユーザーがオフラインの間もGoogleアプリ群を横断してタスクを実行でき、Instacart、OpenTable、Adobe、Shopifyなど40以上の外部サービスとの連携により、食料品の注文やレストラン予約、デザイン作業、ECサイトでの操作まで任せられる。

社内導入の実績としては、10万人超のGoogle従業員が社内版Antigravityを月次で利用し、エンジニアリングチームのエージェント型コード提出は35%増加、コードのロールバックは30%減少したという。Chromeのリファクタリングでは600万行のコードを数カ月かかると見込まれていた作業をわずか数週間で整理し、ADK Pythonフレームワークではセッション準備が40%、コールドインポートが21%高速化、Gemma 4 E2Bではスループットが1秒あたり3万7900トークンから10万8000トークンに向上したとしている。

## 価格競争力と展望

期間限定価格ではArgonは1トークンあたりの単価でClaude Opus 5.5より50%、GPT-6 Astraより80%安く、12月以降の通常価格ではOpus 5.5やMeta Muse Wonderと同水準に並ぶ。Googleはこのほか、1万人の科学者に対してAntigravityの最上位ティーアクセスを6カ月間無償提供する取り組みも進めている。期間限定の低価格設定は競合モデルからの乗り換えを促す狙いが読み取れ、Antigravityとの統合深化を含めた開発者・エンタープライズ双方への浸透戦略が今後の採用動向を左右しそうだ。
