---
date: "2026-11-02T18:12:14+09:00"
title: "GitHub Actions、ホステッドランナーをAzure/AWSのマルチクラウド構成に移行 IP許可リストの更新が必須に"
description: "GitHubはGitHub Actionsのホステッドランナーの一部をAzureとAWSのマルチクラウド構成に移行し、信頼性向上とキュー待ち時間短縮を図ると発表した。"
tags:
  - OSS
  - Cloud
references:
  - "https://github.blog/changelog/2026-10-28-github-actions-adds-multi-cloud-compute-to-improve-reliability/"
---

## 概要

GitHubは10月28日、CI/CDサービス「GitHub Actions」のホステッドランナーについて、これまでMicrosoft Azure単独で提供していた基盤に加えてAmazon Web Services(AWS)も利用するマルチクラウド構成へ移行したと発表した。対象はLinux上の標準的な2コア・4コアランナー、および特殊な設定を伴わない互換性のある大型ランナー(2コア・4コア)で、ジョブは利用可能なクラウドプロバイダーに自動的に振り分けられる。Windowsランナーやプライベートネットワーキング構成、特殊な設定を持つランナーは今回の対象外となる。

## 狙いと背景

今回の変更の目的は、特定のクラウド基盤で発生する障害やピーク時の混雑の影響を一つのプロバイダーに依存しない形で軽減し、ワークフローの起動時間を短縮し、キャパシティ不足によるジョブのキュー待ち時間を減らすことにある。単一クラウドへの依存を解消することで、インフラ全体の信頼性を高める狙いがある。

## 展開方法と必要な対応

展開はGitHub Free、Pro、Teamの各プランでは自動的に有効化される一方、GitHub Enterprise Cloudでは「Enterprise設定 > Actions > Hosted compute cloud providers」からのオプトインが必要となる。移行は段階的(rolling)に進められており、GitHubは組織に対し、ネットワークポリシーを早急に見直すよう推奨している。具体的には、`GET https://api.github.com/meta` で取得できるメタデータの `actions` 配列に含まれる最新のIPレンジをすべてIP許可リストに反映させる必要がある。これを怠ると、認証ブロックや接続障害によってワークフローが失敗する可能性がある。

## 今後の影響

マルチクラウド化により、GitHub Actionsを利用する多くの組織にとっては特別な対応なしに信頼性向上の恩恵を受けられる一方、厳格なネットワーク制御を敷く企業にとってはIP許可リストの管理が新たな運用タスクとして発生する。AWS上のIPレンジがAzureのものに加わることで、CI/CDパイプラインのセキュリティ設定を定期的に見直す運用の重要性が一段と高まったといえる。
