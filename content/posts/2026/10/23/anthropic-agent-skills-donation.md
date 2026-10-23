---
date: "2026-10-23T18:13:39+09:00"
title: "Anthropic、AIエージェント向けオープン標準「Agent Skills」をLinux Foundation傘下AAIFに寄贈"
description: "Anthropicは70以上のプラットフォームで採用され2.8億回インストールされた「Agent Skills」標準を、ベンダー中立な運営のためLinux Foundation傘下のAgentic AI Foundationに寄贈した。"
tags:
  - AI
  - OSS
references:
  - "https://www.anthropic.com/news/donating-agent-skills-to-the-agentic-ai-foundation"
  - "https://www.linuxfoundation.org/press/agentic-ai-foundation-announces-four-new-projects-agent-skills-open-responses-openenv-and-opensandbox"
---

## 概要

Anthropicは10月22日、自社が策定したAIエージェント向けオープン標準「Agent Skills」を、Linux Foundation傘下のAgentic AI Foundation(AAIF)に寄贈すると発表した。Agent Skillsは、SKILL.mdファイルを中心としたフォルダ構成でエージェントに特定のタスクや専門知識を教えるための仕組みで、指示文やスクリプト、参考資料を再利用可能な形でパッケージ化し、エージェントが必要に応じて読み込めるようにする。ChatGPT、Cursor、GitHub Copilot、VS Codeなど70以上のプラットフォームに統合され、公開されているスキルは累計100万件以上、インストール数は2億8000万回近くに達しているという。Anthropicはこの実績を踏まえ、「オープンで、コミュニティ主導、かつベンダー中立」であり続けるという当初からの約束を果たすため、標準の管理を自社から独立した財団に移管する判断に至った。

## 寄贈の背景と技術的な経緯

Anthropicによれば、Agent Skillsを開発する過程で、Claude Codeは一般的な知識作業には十分対応できる一方、実際のビジネスタスクには固有の手順的な知識が必要であることに気づいたという。この課題に対応する形で、スキルを折り畳み可能な知識パッケージとして設計し、エージェントが要求に応じて動的に読み込む仕組みを整えた。Anthropicはこの標準の策定当初からAAIFの共同設立者でもあり、今回の寄贈は特定企業への依存を避け、業界全体で中立的に標準を発展させる狙いがある。今後のロードマップには、バージョン管理されたリリース体系の整備、仕様変更のための正式な提案プロセスの導入、セキュリティに関するガイダンスの提供が含まれ、コミュニティからの参加を優先する方針を示している。

## AAIFの拡大と同時発表の3プロジェクト

Linux Foundationの発表によると、AAIFは2025年12月に3つのプロジェクトでスタートし、発足からわずか1年で、ホストするプロジェクト数を10件まで拡大した。Agent Skillsと同時に、OpenAIが提供する「Open Responses」、Hugging Faceが提供する「OpenEnv」、Alibabaが提供する「OpenSandbox」の3つも新規プロジェクトとして発表された。Open Responsesは複数のLLMプロバイダー間で相互運用可能なインターフェースのオープン仕様で、共有スキーマと一貫したストリーミングイベントを定義し、開発者が異なるモデルプロバイダー間を最小限の変更で移行できるようにする。OpenEnvは強化学習環境構築のためのオープンフレームワークで、コンテナ化されたサービスとして相互運用性とプラグアンドプレイ性、スケーラビリティを実現する。OpenSandboxはAIアプリケーション向けの汎用サンドボックスプラットフォームで、複数言語SDKと統一APIを備え、DockerおよびKubernetesランタイムをサポートする。

## 今後の展望

OpenAI、Hugging Face、Alibabaといった競合も含む主要プレイヤーが同一の財団のもとに標準やフレームワークを持ち込む動きは、AIエージェント分野においてベンダー間の相互運用性を重視する機運が強まっていることを示している。Anthropicの関係者は「Agent Skillsを使って開発する誰もが、その先の方向性を形作ることができる」と述べており、特定ベンダーの独占的な管理から離れることで、エコシステム全体の標準化と採用の加速が期待される。今後、正式な提案プロセスのもとでコミュニティ主導の機能拡張やセキュリティ強化が進むかどうかが、Agent Skillsの普及の次の試金石となりそうだ。
