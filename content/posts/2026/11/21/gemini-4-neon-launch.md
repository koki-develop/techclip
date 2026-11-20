---
date: "2026-11-21T08:07:12+09:00"
title: "Google、「Gemini 4 Neon」を発表 ― Carbon級の品質をFlash並みの速度で、コーディング性能はOpus 5.5に匹敵"
description: "GoogleがGemini 4ファミリーの中位モデル「Neon」を発表し、Opus 5.5級のコーディング性能を25%安いAPI価格で提供する。"
tags:
  - AI
references:
  - "https://blog.google/innovation-and-ai/models-and-research/gemini-models/introducing-gemini-4-neon/"
  - "https://9to5google.com/2026/11/18/gemini-4-neon-announcement/"
  - "https://venturebeat.com/technology/google-launches-gemini-4-neon-with-opus-5-5-level-coding-performance-at-25-lower-api-token-prices"
---

## 概要

Googleは11月18日、「Gemini 4」ファミリーに新たな中位モデル「Gemini 4 Neon」を追加したと発表した。上位モデル「Carbon」に迫る推論品質を、より軽量な「Flash」クラス並みの速度で実現したとされ、複雑なソフトウェアエンジニアリング、エンタープライズ向けの本番ワークフロー、科学分野の分析業務に最適化されている。VentureBeatによれば、コーディング性能はAnthropicのClaude Opus 5.5に匹敵する水準でありながら、APIトークン価格はOpus 5.5より25%低く設定されているという。Neonは当面、Gemini API（Google AI Studio経由）、Gemini for Business、Android Studio、Google Antigravity、有料サブスクライバー向けGeminiアプリなど複数のプラットフォームで段階的に展開される。

## 性能とベンチマーク

各社の報道を総合すると、NeonはArtificial Analysis Intelligence Indexでxhigh思考レベル時に61ポイントを記録し、全体3位につけた。これはCarbon（60）やOpus（59）をわずかに上回る数字である。コーディング領域ではArtificial Analysis Coding Agent Indexで58.6%を獲得し全体1位となったが、VentureBeatが報じたFrontierCode 2.0ベンチマークでは46.2%とOpusの47.3%にわずかに及ばず、Google Antigravity環境下では39.0%まで伸びるなど、評価軸によって結果が分かれている。サイバーセキュリティ分野ではSEC-Bench Proで90.5%という最先端の成績を、競合の大型モデルの約半分のコストで達成したとGoogle自身が強調する。科学的推論ではTerminal-Bench Scienceで70.5%、HLE-Diamondで71.3%を記録し、Vals Indexでも70.9%とSonnet（70.85%）やOpus（70.14%）をわずかに上回ってパレートフロンティアに位置づけられた。処理速度面では出力速度が110トークン/秒とCarbon（59トークン/秒）の約1.9倍に達する一方、最初のトークンが出るまでに約57秒を要するとも報じられている。

## 価格設定とモデルラインアップ

Neonの料金は当初、入力100万トークンあたり3ドル、出力100万トークンあたり15ドルに設定され、キャッシュ入力は0.15ドルと95%の割引が適用される。9to5Googleによると、この価格は11月30日以降に入力4ドル・出力20ドルへ改定される予定で、それでも新価格のArgon（後継としてNeonに置き換えられる）やCarbonより25%安い水準を維持するという。VentureBeatはこの価格設定をClaude Opus 5.5（4ドル/20ドル）と比較し25%安いとする一方、Claude Sonnet 5.5やGPT-6.2 Solよりは50%高いものの、より高い性能で差を正当化していると分析している。モデル選択のピッカーはAuto→Hydrogen→Neon→Carbonという構成に更新され、日常タスク向けのHydrogen、繰り返しの複雑業務向けのNeon、長期プロジェクト向けのCarbonという3段階の階層が明確化された。これに伴い旧モデルの3.1 Proは提供終了となる。

## 今後の展望

Googleは請求書紛争の追跡、ソフトウェアアーキテクチャの理解、機械学習研究における仮説検証、50万以上の数式を含むスプレッドシート生成といった実務ユースケースを例示し、100万トークンのコンテキストウィンドウでビデオ・オーディオ・チャート・スプレッドシート・PDFを混在形式で処理できる点を強みとして打ち出している。Google Cloudの認可サイバーセキュリティパートナー向けには、Fairwind Programを通じた専門版の配布も予定されており、サイバー防御領域での展開が今後の注目点となる。Google DeepMindの技術者らはNeonを「より安価で高速」と位置づけるが、実際の価値は利用環境やワークロードの性質によって変わるとの指摘もあり、Opus 5.5やCarbonとの実運用での比較が今後の評価軸になりそうだ。
