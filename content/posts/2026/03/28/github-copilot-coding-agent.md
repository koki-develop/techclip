---
date: "2026-03-28"
title: "GitHub Copilot利用メトリクスがCoding Agentの使用状況を個別追跡可能に"
description: "GitHub Copilotの利用状況メトリクスが更新され、Copilot Coding Agent（CCA）のアクティブユーザーをIDEのエージェントモードと区別して追跡できるようになった。"
tags:
  - AI
  - OSS
references:
  - "https://github.blog/changelog/2026-03-25-copilot-usage-metrics-now-identify-active-copilot-coding-agent-users/"
---

## 概要

GitHubは2026年3月25日、Copilotの利用状況メトリクスを更新し、Copilot Coding Agent（CCA）のアクティブユーザーを識別・追跡できる機能を追加した。これにより、エンタープライズおよび組織の管理者は、IDE内でのCopilotエージェントモードの利用と、CCAによる自律的なコーディング作業を明確に区別して把握できるようになった。日次および28日間の利用レポートでCCAのアクティブユーザー数を確認でき、チームがIDEの外でどのようにCopilotを活用しているかをデータに基づいて理解できる。

## 技術的な詳細

CCAの利用状況はAPIレスポンス内の`used_copilot_coding_agent`フィールドとして提供される（APIバージョン2026-03-10）。従来からあるIDEエージェントモードの`used_agent`フィールドとは別に管理されるため、2つの異なるエージェント機能の利用状況を個別に分析できる。CCAのアクティビティとしてカウントされるのは、Copilotにissueをアサインした場合と、プルリクエストのコメントで`@copilot`をタグ付けした場合の2つのアクションだ。

## 管理者にとっての意義

今回の更新により、組織の管理者はCopilotの導入効果をより詳細に評価できるようになった。IDEでのコード補完やチャットといった従来の利用に加え、CCAによる自律的な計画・コーディングの利用パターンを把握することで、チーム全体のAI活用状況を包括的にモニタリングできる。これは、Copilotへの投資対効果を測定し、組織内での最適な活用方針を策定するうえで重要なデータとなる。
