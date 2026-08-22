---
date: "2026-08-22T20:03:14+09:00"
title: "GitHub Copilot、SlackとTeamsでチーム共同作業型のエージェントセッションをプレビュー公開"
description: "GitHubがSlackとMicrosoft Teams上で「@GitHub」とメンションしてCopilotエージェントを起動し、チームで共同作業できる新機能をパブリックプレビュー公開した。"
tags:
  - OSS
  - AI
references:
  - "https://github.blog/changelog/2026-08-21-the-new-github-copilot-experience-in-slack/"
  - "https://github.blog/changelog/2026-08-21-shared-agentic-work-with-github-copilot-in-microsoft-teams/"
---

## 概要

GitHubは2026年8月21日、SlackおよびMicrosoft Teams上でCopilotのエージェントセッションを起動できる新機能をパブリックプレビューとして公開した。いずれのプラットフォームでも「@GitHub」とメンションするだけでエージェントセッションが始まり、コードに関する質問への回答、バグ報告のトリアージ、問題調査、コード変更の実装、プルリクエスト（PR）の作成までをチャット上から非同期に実行できる。従来、開発に関する意思決定はミーティングやチャットで交わされた後、実際の作業はIDEやターミナルに場所を移して行う必要があったが、今回の機能によって会話の流れの中でそのまま作業を開始できるようになる。

## Slackでの体験

Slack版の大きな特徴は、エージェントセッションが「共有」されている点にある。GitHubのブログでは "Agent sessions in Slack are shared, so your team can collaborate on the work" と説明されており、一人がCopilotに指示を出したセッションを、チームメンバー全員が閲覧・介入できる。Copilotは会話内容と許可されたGitHubのコンテキストを踏まえて質問に回答し、必要に応じて専用の「コードチャンネル」を作成する。このチャンネル上ではdiffの確認や生成物のプレビューをチーム全体で検討できるため、コードレビューに近い共同作業がチャットツール上で完結する。作成されたPRは会話にリンクされ、リポジトリ管理者はマージ前に追加の承認を必須化する設定も可能だ。

## Teamsでの体験

Microsoft Teams版も同様に「@GitHub」メンションでエージェントセッションを開始できる設計だが、想定されている利用シーンとして強調されているのは会議中の即時実行だ。GitHubは "everyone sees the agents investigation together and can direct it further if needed" と述べており、会議で出た決定事項をその場でCopilotに調査・実装させ、参加者全員が経過を見ながら追加の指示を出せる。利用にはTeams上でGitHubアプリをインストールし、GitHubアカウントを接続する必要がある。

## 技術的な詳細と提供条件

両機能とも、Copilotが担当したタスクはクラウド上のサンドボックス環境で非同期に処理される仕組みで、チャットで開始した作業をIDEやターミナルから引き継いで続行することも可能だ。提供対象はGitHub Copilot Business/Enterpriseなどの有料プランで、Teams版はAIクレジットを消費する形で課金され、組織単位での使用量ベースの予算管理にも対応する。いずれのプラットフォームでも、リポジトリ管理者はエージェントが作成したPRのマージに人間の承認を必須とするコンプライアンス設定を有効化でき、"a human in the loop before agent-authored work ships" というエンタープライズ向けの安全策が組み込まれている。

## 背景と今後の展望

今回の発表は、GitHub Copilotが単なるコード補完ツールから、チームのコラボレーションツール上で動く非同期エージェントへと役割を広げる流れの一環と位置づけられる。SlackやTeamsといった日常的なコミュニケーション基盤にエージェント機能を統合することで、意思決定から実装までのリードタイム短縮を狙う一方、承認フローや使用量管理などエンタープライズ導入を意識した機能も同時に整備されている点が特徴的だ。両機能とも現時点ではパブリックプレビューであり、今後のフィードバックを踏まえた機能拡張や正式提供が見込まれる。
