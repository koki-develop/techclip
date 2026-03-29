---
date: "2026-03-30"
title: "AmazonがAI健康エージェント「Health AI」を一般展開、マルチエージェント構成でPrimeメンバーに無料医療相談も提供"
description: "AmazonがOne Medical向けに提供していたAI健康エージェント「Health AI」をAmazonウェブサイトとアプリに拡大展開し、Primeメンバーには最大5回の無料医療相談を提供する。"
tags:
  - AI
references:
  - "https://www.aboutamazon.com/news/retail/amazon-health-ai-agent-one-medical"
  - "https://techcrunch.com/2026/03/10/amazon-launches-its-healthcare-ai-assistant-on-its-website-and-app/"
  - "https://hlth.com/insights/news/amazon-launches-health-ai-agent-on-its-website-expands-free-virtual-care-to-200m-prime-members-2026-03-16"
---

## 概要

Amazonは2026年3月、AI健康エージェント「Health AI」をAmazon.comおよびAmazonアプリに展開した。Health AIは健康に関する質問への回答、医療記録や検査結果の解説、Amazon Pharmacyを通じた処方箋の更新管理、One Medical医師との予約手配など、幅広い健康関連タスクに対応するエージェント型AIアシスタントである。もともと2026年初頭にOne Medicalアプリ限定で提供されていたが、今回の拡大により、PrimeメンバーやOne Medical会員でなくても利用可能となった。米国内の全ユーザーへの展開を数週間以内に完了する予定としている。

## マルチエージェントアーキテクチャ

Health AIはAmazon Bedrock上で動作するマルチエージェントシステムとして構築されている。患者と直接対話する「コアエージェント」、処方箋管理や予約手配などの個別ワークフローを担当する「サブエージェント」、会話をリアルタイムで安全性チェックする「オーディターエージェント」、そしてシステム全体を監視し必要に応じて人間の医療提供者へエスカレーションする「センチネルエージェント」の4層構成となっている。タスクに応じて異なるAIモデルを柔軟に使い分ける設計で、臨床上の安全性が不確実な場合は人間の医師に判断を委ねる仕組みが組み込まれている。

## パーソナライズと医療データ連携

Health AIは個人の医療データなしでも一般的な健康相談に対応できるが、ユーザーがOne Medicalに対してHealth Information Exchange（全米の医療情報共有ネットワーク）経由での医療記録アクセスを許可すると、診断歴、服用中の薬、検査結果、臨床ノートを踏まえた個別化された回答が可能になる。すべてのやり取りはHIPAA準拠の環境内で行われ、会話は暗号化され厳格なアクセス制御の下で保護される。One MedicalやAmazon Pharmacyの保護対象健康情報はAmazonの一般商品マーケティングや広告には使用されず、個人データの第三者販売も行わないとしている。

## Primeメンバー向け特典と料金体系

米国のPrimeメンバーには導入特典として、One Medical医師による最大5回の無料ダイレクトメッセージ相談が提供される。対象は風邪、インフルエンザ、アレルギー、尿路感染症、結膜炎など30以上の一般的な症状で、約145ドル相当の価値があるとしている。この特典はAmazon Familyを通じて家族メンバーとも共有可能である。一般ユーザーはOne Medicalの遠隔医療を1回29ドルの都度払いで利用でき、治療プラン確定後14日間は無制限のフォローアップメッセージが可能となっている。

## 競合環境と今後の展望

消費者向けAIヘルスケア市場では大手テック企業の参入が相次いでいる。OpenAIは患者向けの「ChatGPT Health」を、Anthropicは医療提供者・保険者向けの「Claude for Healthcare」をそれぞれ発表しており、MicrosoftもCopilot Healthで医療記録とウェアラブルデータを統合するAIアシスタントを展開している。AmazonはOne Medical（2023年に39億ドルで買収）やAmazon Pharmacyなどの既存ヘルスケアインフラとの統合を強みとしており、Rush University System for HealthやCleveland Clinicなどの医療機関とも提携してプライマリケアから専門医療へのシームレスな連携を実現している。Health AIの開発チームは「AIは医療における人間のつながりを置き換えるのではなく強化する」と位置づけており、管理業務の効率化を通じて患者と医師がより有意義な関係を築く時間を確保することを目指している。
