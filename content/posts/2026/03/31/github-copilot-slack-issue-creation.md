---
date: "2026-03-31"
title: "GitHub CopilotのSlack連携でIssueを自然言語で即作成、親子タスク構造にも対応"
description: "GitHub CopilotとSlackが連携し、Slackチャンネルから自然言語でGitHub Issueを直接作成できる機能が追加された。"
tags:
  - AI
  - OSS
references:
  - "https://github.blog/changelog/2026-03-30-create-issues-from-slack-with-copilot/"
---

## 概要

GitHubは2026年3月30日、Slackから自然言語を使ってGitHub Issueを直接作成できる新機能を発表した。SlackチャンネルでGitHubアプリに`@GitHub`とメンションし、作業内容をプレーンな言葉で説明するだけで、タイトル・本文・担当者・ラベル・マイルストーンといった情報を含む構造化されたIssueが自動生成される。チームがすでに議論を行っているSlack上から離れることなく、開発タスクの登録・管理ができるようになる。

この機能はGitHub Copilotの全プランで利用可能であり、Slackワークスペースへの既存GitHubアプリのインストールまたはアップグレードのみで使い始められる。

## 主な機能と使い方

作成されるIssueは単純な1件に限らず、1つのメッセージから**親Issue（Epic）と子Issue（サブタスク）の両方**を一度に生成する階層的なタスク管理にも対応している。また、Slackのスレッド内で`@GitHub`と対話を続けることで、Issue登録前に内容を対話的に調整することも可能だ。

チャンネル単位の設定も用意されており、`@GitHub settings`コマンドを使うことで、そのチャンネルで作成されるIssueやプルリクエストのデフォルトリポジトリをあらかじめ指定できる。利用開始の手順は次のとおりだ。

1. GitHub Copilotを有効化する（全プラン対応）
2. Slackワークスペースに GitHubアプリをインストールまたはアップグレードする
3. チャンネルで`@GitHub`をメンションし、例えば「Create an issue in my-org/my-repo to add dark mode support」のように指示を入力する

## 背景と意義

開発チームにとって、SlackでのディスカッションとGitHub上のタスク管理は往々にして分断されがちだった。重要な決定事項や作業依頼がSlackのスレッドに埋もれ、Issueとして記録されないまま忘れられるケースは少なくない。今回の機能統合により、会話の流れを途切れさせることなくリポジトリへの作業登録が行えるようになり、チームのワークフロー全体の効率向上が期待される。GitHub Copilotがコード補完を超えて開発プロセス全体に浸透しつつある流れを示す取り組みといえる。
