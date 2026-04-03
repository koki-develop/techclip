---
date: "2026-04-04T02:16:45+09:00"
title: "MicrosoftがMAI独自基盤モデル3種を発表——音声認識・音声合成・画像生成でOpenAI・Googleに真っ向勝負"
description: "MicrosoftのAI部門（MAI）が音声認識「MAI-Transcribe-1」、音声合成「MAI-Voice-1」、テキスト画像生成「MAI-Image-2」の3モデルをMicrosoft Foundryで公開プレビュー開始し、主要ベンチマークでOpenAIやGoogleを上回る性能を示した。"
tags:
  - AI
references:
  - "https://techcrunch.com/2026/04/02/microsoft-takes-on-ai-rivals-with-three-new-foundational-models/"
  - "https://venturebeat.com/technology/microsoft-launches-3-new-ai-models-in-direct-shot-at-openai-and-google"
  - "https://www.business-standard.com/technology/tech-news/microsoft-introduces-mai-transcribe-1-voice-1-image-2-ai-models-features-126040300584_1.html"
---

## 概要

Microsoftは2026年4月2日、AI部門「Microsoft AI（MAI）」が独自開発した3つの基盤モデルをMicrosoft Foundryで公開プレビュー開始した。音声認識モデル「MAI-Transcribe-1」、音声合成モデル「MAI-Voice-1」、テキスト画像生成モデル「MAI-Image-2」の3種で、いずれもすでにCopilot・Bing・PowerPointなど自社製品で実運用されてきたモデルを外部向けに開放する形となっている。MAI部門はMustafa Suleyman CEOの下で約6か月前に発足した組織であり、OpenAIやGoogleへの依存を減らしながらエンタープライズAI市場での自立と競争力強化を図る「AI自給自足」戦略の一環として今回の発表が位置づけられている。

## 各モデルの性能と技術仕様

**MAI-Transcribe-1**（音声認識）は25言語に対応した音声文字起こしモデルで、FLEURSベンチマークの上位25言語における平均単語誤り率（WER）3.8%を達成。OpenAIのWhisper-large-v3を全25言語で上回り、GoogleのGemini 3.1 Flashは25言語中22言語で超える。従来のAzure Fast比で2.5倍高速かつGPUコストを約50%削減しており、価格は$0.36/時間（音声）から。IVRシステム・コールセンターのリアルタイム文字起こしや、ライブキャプション・メディア字幕自動化などの用途を想定している。

**MAI-Voice-1**（音声合成）は単一GPUで60秒分の高品質音声を1秒以内に生成できる高効率アーキテクチャを採用。10秒の音声サンプルからカスタムボイスを作成できる「Personal Voice」機能を備え、責任あるAIポリシーに基づく承認プロセスを経て利用可能。CopilotのVoice機能やポッドキャスト生成機能をすでに駆動しており、価格は$22/100万文字から。

**MAI-Image-2**（テキスト画像生成）はMicrosoftの最高性能テキスト画像モデルで、Arena.aiのリーダーボードで画像モデルファミリー部門3位にデビュー。写実的な画像生成に加え、画像内テキストのレンダリング精度と複雑なレイアウト対応を強みとする。WPP（大手マーケティング企業）がキャンペーン向けクリエイティブワークフローの自動化に採用しており、価格はテキスト入力$5/100万トークン、画像出力$33/100万トークン。

## 戦略的背景と今後の展望

これらモデルはMicrosoft Foundryおよび新設された「MAI Playground」を通じて即日アクセス可能となっており、開発者はAPIを通じた本番統合も可能だ。MAI-Transcribe-1とMAI-Voice-1を言語モデルと組み合わせることで、音声エージェントの構築も実現できるとMicrosoftは説明している。今回の発表はOpenAIとの長年のパートナーシップを維持しながらも、モデル調達の多様化を図るMicrosoftの方針転換を象徴するものとして業界から注目されている。CohereやMistralなどオープンソース勢も音声認識分野で競合性能を持つモデルを投入しており、基盤モデル市場の競争はさらに激化する見通しだ。