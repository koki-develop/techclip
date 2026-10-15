---
date: "2026-10-16T08:09:33+09:00"
title: "xAI、音声AI「Grok Voice 3.0」を発表 Speech-to-Speech指数でOpenAI・Googleを上回る"
description: "xAIが新型音声対話AIモデル「Grok Voice 3.0」を発表し、独立機関のベンチマークでOpenAIやGoogleの競合モデルを上回る性能を示すとともに、Tesla車載システムやStarlinkのカスタマーサポート業務で既に実運用されていることが明らかになった。"
tags:
  - AI
references:
  - "https://x.ai/news/grok-voice-3"
  - "https://siliconangle.com/2026/10/14/grok-voice-3-0-from-spacexsi-outscores-openai-and-google-on-speech-to-speech-index/"
  - "https://www.techrepublic.com/article/news-spacexsi-grok-voice-3-ai-customer-support/"
---

## 概要

xAIは10月14日、新型音声対話AIモデル「Grok Voice 3.0」を発表した。同社は本モデルを「世界で最も知能の高い音声モデル」と位置づけており、独立評価機関Artificial Analysisによるテストでは、音声対音声の総合性能を示すSpeech-to-Speech Indexで86.9点を記録し、OpenAIのGPT-Live-1（83.2点）やGoogleのGemini 3.8 Live（82.6点）を上回って業界トップに立った。なお一部の報道ではxAIが「SpaceXSI」（旧xAI）の名称でも言及されており、Elon Musk氏が率いる企業体制の変化を反映しているとみられる。

## 性能面での優位性

Grok Voice 3.0は複数のベンチマークで高い評価を獲得している。自然な会話のターンテイキングや割り込み処理を評価するFull Duplex Benchでは97%、音声推論能力を測るBig Bench Audioでは98.5%を記録した。タスク成功率は94.8%に達し、ServiceNowが提供する企業向け評価指標EVA-Benchでも74%という最高精度を達成している。応答速度では1秒未満のレイテンシを実現し、競合モデルと比べて約40%短縮したという。多様なアクセントや背景ノイズ、割り込みへの耐性を測るτ-Voiceでは71.6%の成功率を示した。コスト面でも優位性を強調しており、タスクあたりの平均コストは約2.5セントで、OpenAIの約3セントや旧世代のGPT-Realtime-2.1の5.5セントを下回るとしている。

## Tesla・Starlinkでの実運用

Grok Voice 3.0は発表時点で既に実運用が進んでいる点も特徴だ。Tesla車両では、運転者がハンズフリーで操作できる車載音声アシスタントとして日々数百万件規模の音声会話を処理しているという。衛星インターネット事業のStarlinkでは、カスタマーサポート業務に導入され、1日あたり約20,000件の顧客対応を複数言語で処理。そのうち70%は人間の介入なしに解決され、営業関連の通話では4件に1件が購入につながっているとされる。実際の商用環境における大規模運用データは、音声AIの実用性を示す裏付けとして注目されている。

## 価格と今後の展望

Grok Voice 3.0はAPI経由で本日より利用可能となり、価格は1分あたり0.08ドル（時間単位で4.80ドル）で、前バージョンから変更はない。既存ユーザー向けには`grok-voice-latest`エイリアスを通じた自動切り替えにも対応する。企業のカスタマーサポートや営業電話対応といった実務領域での性能と応答速度の両立を打ち出したことで、音声AI市場における競争はさらに激化しそうだ。OpenAIやGoogleが追随して新モデルを投入するかどうかが、今後の焦点となる。
