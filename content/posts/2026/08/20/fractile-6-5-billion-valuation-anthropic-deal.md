---
date: "2026-08-20T20:05:39+09:00"
title: "英AIチップ企業Fractile、Anthropicとの2.5億ドル供給契約を機に評価額65億ドルの資金調達へ"
description: "英国のAI推論チップ新興企業FractileがAnthropicとの約2.5億ドル相当のチップ供給契約を機に、評価額65億ドルで約6億ドルの資金調達交渉を進めていると報じられた。"
tags:
  - AI
  - Other
references:
  - "https://www.bloomberg.com/news/articles/2026-08-19/ai-chip-startup-fractile-in-talks-for-6-5-billion-value-after-anthropic-deal"
  - "https://www.vktr.com/ai-news/uk-chip-startup-fractile-nears-65-billion-valuation-after-landing-250-million-anthropic-deal/"
  - "https://thenextweb.com/news/fractile-6-5bn-valuation-anthropic-chip-deal"
---

## 概要

ロンドン拠点のAI推論チップ新興企業Fractileが、AnthropicへのチップサプライヤーとしてFractileのチップを供給する契約を締結したことを機に、企業価値65億ドルで約6億ドルを調達する交渉を進めていることが明らかになった。この評価額は、わずか3か月前の2026年5月に2.2億ドル規模の資金調達（評価額約10億ドル）を実施した際の6倍以上に相当する急騰である。なお2026年5月のラウンドはAccel、Founders Fund、Factorial Fundsが主導し、前Intel CEOのPat Gelsinger氏もエンジェル投資家として参加していたが、今回の新ラウンドの投資家については明らかになっていない。

## Anthropicとの契約内容

FractileはAnthropicとの間で、約2.5億ドル相当のチップを供給する初期契約を締結し、将来的な契約拡大も視野に入れている。ただし、実際にチップが実装可能になるのは2027年からとされ、現時点では量産出荷前の段階にある。これによりAnthropicは、Google のTPU、Amazon のTrainium、Broadcom に続く4番目の主要チップサプライヤーを確保することになる。大手AI企業がNvidiaへの依存を減らすべく調達先を分散させる動きの一環であり、Fractileの契約獲得はその象徴的な事例となっている。

## 技術的な特徴

2022年にオックスフォード大学のロボティクス研究者Walter Goodwin氏が設立したFractileは、モデルの訓練が完了した後、個々のリクエストに応答する処理である「推論（inference）」に特化したチップ設計を手がけている。同社は「メモリ・コンピュート融合」と呼ばれる手法を採用し、コンピュートとメモリを同一ダイ上に配置してSRAMを利用することで、別チップへのデータ取得（オフチップアクセス)にともなう遅延を回避する設計としている。同社は既存ハードウェアと比較して大規模言語モデルの実行速度を最大100倍高速化し、運用コストを90%削減できると主張しているが、本番環境での性能は第三者による独立検証がまだ行われていない点には留意が必要である。

## 背景と今後の展望

今回の評価額急騰は、Etched や Groq、Cerebras といった推論特化型チップ新興企業が相次いで高額な評価を獲得している業界全体の潮流を反映したものだ。チャットボットやAIエージェントの応答速度向上に加え、医薬品や材料開発など高速な推論を要する用途への展開も見込まれている。一方で、Fractileの評価額は未発表の製品と単一の大口顧客契約に大きく依存しており、2027年の量産開始までに技術面・実行面でのリスクが解消されるかが今後の焦点となる。
