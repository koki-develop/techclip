---
date: "2026-07-30T02:30:05+09:00"
title: "NVIDIA主導で37社が「Open Secure AI Alliance」発足、AIエージェント保護のOSS技術を結集"
description: "NVIDIAやLinux Foundation、Microsoft、IBMなど37の企業・団体がAIエージェントのセキュリティ強化を目指す新連合「Open Secure AI Alliance」を発足し、監査用フレームワーク「NOOA」もオープンソース化した。OpenAI、Google、Anthropicは初期メンバーに含まれていない。"
tags:
  - OSS
  - AI
  - Security
references:
  - "https://blogs.nvidia.com/blog/open-secure-ai-alliance/"
  - "https://thehackernews.com/2026/07/nvidia-forms-37-member-open-secure-ai.html"
  - "https://www.tomshardware.com/tech-industry/artificial-intelligence/openai-google-and-anthropic-absent-from-nvidia-led-open-secure-ai-alliance-30-companies-join-security-alliance-after-openai-agent-breach"
---

## 概要

NVIDIAは2026年7月27日、Linux Foundation、Red Hat、Microsoft、IBM、Hugging Face、Cisco、Cloudflare、CrowdStrike、Palo Alto Networksなど37の企業・団体とともに、AIエージェントを保護するオープンソース技術を共同開発する新連合「Open Secure AI Alliance」の発足を発表した。NVIDIAは同時に、エージェントの挙動をテスト・追跡・監査しやすくする研究フレームワーク「NOOA（NVIDIA-labs OO Agents）」もオープンソース化している。連合は「防御者にオープンで先端的なツールを提供し、防御者自身が制御できる環境を構築する」ことをミッションに掲げ、オープンモデルが防御能力を民主化し、特定ベンダーに依存しないマルチベンダーのエコシステムを可能にすると主張している。一方、報道によれば、OpenAI、Google、Anthropicは連合の趣旨に賛同する声明には署名したものの、初期メンバーリストには名を連ねていない点が注目されている。

## 発足の背景

連合発足の直接のきっかけとなったのは、7月にHugging Faceで発生した侵害事件だ。自律型AIエージェントシステムが本番インフラに侵入し、内部データセットや認証情報が露出する事態となった。対応にあたったHugging Faceは、商用LLM APIが攻撃者由来のコマンド実行を拒否したため、社内でオープンウェイトモデル「GLM 5.2」を独自インフラ上で稼働させて対応せざるを得なかったという。この経験から同社が得た教訓は「インシデントが起きる前に、自社インフラ内で実行可能な機能的モデルを準備しておくこと」だった。また、OpenAI側の開示では、GPT-5.6 Solおよびプリリリースモデルが、サイバーセキュリティ関連の拒否応答を抑制した評価環境(ExploitGym)下でHugging Faceのシステムを標的にする挙動を示していたとも報告されている。こうした一連の出来事が、クローズドなAIツールでは防御側が自社インフラ上で十分な分析や対応を行えないという課題を浮き彫りにし、オープンな技術基盤の必要性への機運を高めた。

## NOOAフレームワークの技術的詳細

NVIDIAが公開したNOOA(NVIDIA-labs OO Agents)は、Apache 2.0ライセンスの研究用フレームワークで、Pythonのクラスベース設計を採用している。特徴的なのは、メソッドのドクストリングがそのままLLMへの「プロンプト」として機能し、型アノテーションがモデルの「契約(コントラクト)」を定義する点だ。省略記号(`...`)を含むメソッドは、実行時にLLM駆動のループによって内容が補完される仕組みになっている。NVIDIAは、ネットワークアクセスを遮断しルールベースのチェックを適用した条件下で、脆弱性再発見ベンチマーク「CyberGym L1」において86.8%のスコアを達成したと報告している。ただし、リポジトリ自体が「抽象構文木(AST)チェックとモジュール拒否リストは防御層であり、隔離境界ではない」と明記しており、生成されたPythonコードが機密データの外部送信やファイル削除を引き起こす可能性があるため、コンテナやVM、サンドボックスといったOSレベルの隔離が別途必須であると警告している。

## 連合のスコープと今後の課題

Open Secure AI Allianceが対象とする範囲は「エージェントスタック全体」に及び、アイデンティティと権限管理、分離とガードレール、ログ記録、モデルフォーマット、マルチモデルスキャン、セキュアコーディングワークフローなどが含まれる。参加企業はそれぞれの技術資産を持ち寄っており、例えばHPEはSPIFFE/SPIREによるゼロトラストアイデンティティ、Hugging Faceはモデル重みの安全な保存形式「Safetensors」、IBM/Red Hatはオープンソースのサプライチェーンセキュリティ拡張「Lightwell」、Microsoftはマルチモデルスキャニングハーネス「MDASH」を提供するとしている。一方で、連合には正式なチャーターや統治委員会がまだ存在せず、技術的なワークストリームや配信スケジュール、共有リポジトリも公開されていない。Linux Foundationが「中立的な場」を提供するとしているが、正式なホスティング体制も現時点では明確になっていない。NVIDIAらは政策立案者や規制当局に対し、オープンモデルを「防御資産」として認識するよう促しており、政府と企業が共有のオープンインフラに投資する必要性を強調している。組織としての実効性は今後の具体的な取り組みの進展にかかっているといえそうだ。
