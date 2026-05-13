---
date: "2026-05-14T02:46:39+09:00"
title: "GitHub Enterprise Live Migrationsがパブリックプレビュー公開、ダウンタイムほぼゼロでCloudへ移行可能に"
description: "GitHubがEnterprise Live Migrations (ELM) のパブリックプレビューを開始し、GitHub Enterprise ServerからEnterprise Cloudへの移行を開発者の作業を止めることなく数分で完了できるようになった。"
tags:
  - OSS
references:
  - "https://github.blog/changelog/2026-05-07-enterprise-live-migrations-is-now-in-public-preview/"
---

## 概要

GitHubは2026年5月7日、**GitHub Enterprise Live Migrations (ELM)** のパブリックプレビューを開始した。ELMはGitHub Enterprise Server (GHES) からGitHub Enterprise Cloud（データレジデンシー対応）へのリポジトリ移行を、ほぼダウンタイムなしで実施できる新機能だ。従来の移行では数日かかるカットオーバーが必要だったのに対し、ELMでは「数日ではなく数分」でのカットオーバーを実現し、地理的に分散したチームでも業務中断を最小限に抑えることができる。

## 主な特徴と技術的な詳細

ELMの最大の特徴は、移行中も開発者が通常通り作業を継続できる点にある。データは継続的に同期されるため、カットオーバー直前まで両環境間の差分が自動的に埋められ続ける。また、深いGit履歴を持つ巨大なモノレポや、大量のIssues・Pull Requestsを抱えるリポジトリにも対応しており、リソースレベルの進捗追跡によって移行前に問題を事前検出することも可能だ。

技術的には、ELMはGHESアプライアンス上でサービスとして動作し、`elm` CLIコマンドで制御する。対応するGHESバージョンは3.17.14以降、3.18.8以降、3.19.5以降、3.20.2以降となっている。また、既存のGitHub Enterprise Importer (GEI) とも統合して使用でき、各リポジトリの特性に応じて最適なツールを選択する柔軟な運用が可能だ。

## 今後の展望

ELMはパブリックプレビュー段階であり、今後フィードバックを基に改善が進む見込みだ。企業がオンプレミス環境からクラウドへの移行を検討する際の主要な障壁であった「移行中の業務停止リスク」を大幅に低減することで、GHES利用企業のクラウド移行加速につながると期待されている。
