---
date: "2026-03-30"
title: "AmazonがAI健康エージェント「Health AI」を一般公開、2億人超のPrime会員に無料バーチャル診療も提供"
description: "Amazonが自社サイトとアプリでAI健康エージェント「Health AI」を公開し、Prime会員向けにOne Medical医師とのダイレクトメッセージによる無料診療を最大5回提供する。"
tags:
  - AI
references:
  - "https://www.aboutamazon.com/news/retail/amazon-health-ai-agent-one-medical"
  - "https://techcrunch.com/2026/03/10/amazon-launches-its-healthcare-ai-assistant-on-its-website-and-app/"
  - "https://www.fiercehealthcare.com/ai-and-machine-learning/amazon-launches-health-ai-assistant-its-website-expands-free-virtual-care"
---

## 概要

Amazonは2026年3月、AI健康エージェント「Health AI」をAmazon.comおよびAmazonアプリ上で一般公開した。Health AIは2026年1月にOne Medicalアプリ内で先行提供されていたが、今回の拡大により米国のすべての顧客がアクセス可能となる。PrimeメンバーやOne Medical会員でなくても利用でき、一般的な健康相談から医療記録に基づくパーソナライズされたアドバイスまで、24時間365日対応する。

対象となる米国Prime会員には、導入特典としてOne Medicalの医師とのダイレクトメッセージによるバーチャル診療が最大5回無料で提供される。対応する症状は風邪・インフルエンザ、アレルギー、逆流性食道炎、結膜炎、尿路感染症など30種類以上で、最大145ドル相当のサービスとなる。Amazon Familyの家族メンバーも同様の特典を受けられる。Prime会員以外は1回29ドルの従量課金か、年間199ドル（Prime会員は99ドル）のOne Medicalメンバーシップで利用可能だ。

## マルチエージェントアーキテクチャ

Health AIの技術基盤にはAmazon Bedrockが採用されており、タスクに応じて異なる基盤モデルを使い分けるマルチエージェントシステムとして構築されている。Amazon Health ServicesのCTO Prakash Bulusu氏によれば、患者と対話するコアエージェント、特定のワークフローを処理するサブエージェント、会話をリアルタイムで監視する監査エージェント、そしてシステム全体を監視する見張り役のセンチネルエージェントが連携して動作する。臨床的に不確実な場面では人間の医療提供者へのエスカレーションパスが確保されており、デプロイ前には合成データを用いた臨床安全性・緊急対応・コンプライアンスに関する広範な評価が実施された。

具体的な機能としては、州の医療情報交換ネットワークを通じて患者の診断歴・処方薬・病歴にアクセスし、検査結果の解釈、処方箋の更新管理、医療予約の手配、さらにはAmazon.comでの関連製品の提案まで行う。すべてのやり取りはHIPAA準拠の環境で暗号化され、One MedicalやAmazon Pharmacyの保護対象医療情報がAmazonの一般商品マーケティングや広告に使用されることはないとしている。

## 競争環境と今後の展望

消費者向けAIヘルスケア市場は急速に過熱しており、OpenAIの「ChatGPT Health」、Anthropicの「Claude for Healthcare」、Microsoftの「Copilot Health」などが相次いで登場している。Forresterのアナリスト Arielle Trzcinski氏は「AIを活用したヘルスケア体験の普及は先行者利益の競争であり、ビッグテックが勝っている」と指摘する。Amazonの強みは、2023年に39億ドルで買収したOne Medicalとの統合により、AIによるガイダンスから実際の臨床ケアまでをプラットフォーム内で完結できる点にある。

今後Amazonは、Rush大学、Cleveland Clinic、Montefiore、Hackensack Meridian Healthなどとの提携を通じて、プライマリケアから専門医への紹介までシームレスにつなぐ専門ケア連携の拡充を計画している。栄養、運動、継続的な健康管理に関するAI支援ガイダンスの追加も予定されており、Amazon Health ServiceのCTO Bulusu氏は「初めて、本当にパーソナルな健康エージェントをポケットに入れられるようになった。24時間利用可能で、実際の医療提供者がバックアップしている」と語っている。
