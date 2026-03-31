---
date: "2026-04-01"
title: "Cohereが20億パラメータのオープンソースASRモデル「Transcribe」を公開、Hugging Faceリーダーボードでトップ水準を達成"
description: "エンタープライズAI企業のCohereが初の音声認識モデル「Cohere Transcribe」をオープンソースで公開し、Hugging Face Open ASRリーダーボードで平均単語誤り率5.42%を記録して競合モデルを上回った。"
tags:
  - AI
  - OSS
references:
  - "https://techcrunch.com/2026/03/26/cohere-launches-an-open-source-voice-model-specifically-for-transcription/"
  - "https://www.marktechpost.com/2026/03/26/cohere-ai-releases-cohere-transcribe-a-sota-automatic-speech-recognition-asr-model-powering-enterprise-speech-intelligence/"
---

## 概要

エンタープライズAIを手がけるCohereが2026年3月26日、同社初の音声モデルとなる自動音声認識（ASR）モデル「Cohere Transcribe」をオープンソースとして公開した。Hugging Face Open ASRリーダーボードでは平均単語誤り率（WER）5.42%を達成し、Zoom Scribe v1やElevenLabs Scribe v2といった競合モデルを上回る精度を示している。これまでテキスト生成・検索・RAGを中心に展開してきたCohereにとって、音声AI領域への初参入となる。

## 技術的な詳細

Cohere Transcribeは20億（2B）パラメータという比較的軽量なアーキテクチャを採用しており、14言語の音声認識に対応している。モデルの実行にはコンシューマーグレードのGPUで十分なため、高価なエンタープライズ向けインフラを必要としない。オープンソースとして公開されているため、ユーザーは自社環境でのセルフホストが可能で、クラウドAPIへの依存を排除しながらモデルのカスタマイズや微調整を行えるのが特徴だ。

## エンタープライズ向けの訴求点

Cohereはこれまでも企業のプライバシー要件やオンプレミス展開ニーズに応える製品ラインナップを強みとしており、Cohere TranscribeもそのコンセプトをASR領域に持ち込んだ形となる。会議の文字起こし、コールセンターの音声解析、多言語コンテンツの自動字幕生成など、エンタープライズ用途での活用が想定される。コンシューマーGPUでの動作やセルフホスト対応により、データをクラウドに送信できないセキュリティ要件の厳しい業界でも採用しやすい設計となっている。

## 音声AI市場への参入と今後の展開

音声認識市場ではOpenAI Whisper、Google Speech-to-Text、AssemblyAIなど多くのプレイヤーが競合しているが、Cohereはエンタープライズ向けのセルフホスト対応と高精度の組み合わせで差別化を図る。オープンソース公開によるコミュニティへの貢献と、エンタープライズ向けサポートサービスによる収益化という二軸の戦略は、同社の既存製品と共通するアプローチだ。今後は対応言語数の拡大やドメイン特化モデルの提供など、さらなる展開が期待される。
