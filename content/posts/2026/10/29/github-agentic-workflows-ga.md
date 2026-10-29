---
date: "2026-10-29T18:10:50+09:00"
title: "GitHub、MarkdownでAIエージェントを自動化する「GitHub Agentic Workflows」を正式リリース"
description: "GitHub Nextが開発したオープンソースプロジェクト「GitHub Agentic Workflows」がGAとなり、自然言語のMarkdownからGitHub Actions上で動くエージェント自動化を記述できるようになった。"
tags:
  - OSS
references:
  - "https://github.blog/changelog/2026-10-28-github-agentic-workflows-generally-available/"
---

## 概要

GitHubは10月28日、研究開発部門GitHub Nextが手がけていたオープンソースプロジェクト「GitHub Agentic Workflows」を正式提供(GA)したと発表した。これまでプレビュー段階だった同プロジェクトは、Issueのトリアージ、CI失敗の分析、ドキュメントの更新、テストの作成といった定型的だが手間のかかる作業を、GitHub Actions上で動くコーディングエージェントに委ねる仕組みを提供する。開発者は自然言語でタスクをMarkdownファイルに記述するだけでよく、システムがその内容を標準的なActions YAMLへ自動的にコンパイルする。エージェントの実行基盤にはGitHub Copilotまたはカスタムのコーディングエージェントを利用できる。

## セキュリティとガバナンスの仕組み

自動化されたエージェントをCI/CD環境で動かす以上、権限や実行環境の安全性が課題となるが、GitHub Agentic Workflowsは複数層のセーフガードを組み込んでいる。具体的には、整合性フィルタールールの尊重、デフォルトでの読み取り専用権限、サンドボックス化されたコンテナでの実行に加え、専用の「Agent Workflow Firewall」や安全な出力処理プロセス、脅威検知専用のジョブなどが用意されている。これにより、エージェントが意図しない書き込みや外部への情報漏洩を起こすリスクを抑えつつ、リポジトリ内での自律的な作業を可能にしている。

## GAで追加された機能と利用環境

正式提供にあわせて、Actions Runner Controller(ARC)およびDocker-in-Dockerのサポート、予算予測機能`gh aw forecast`の改善、新しいモデルやワークフローテンプレート、モデルルーティング機能、さらにCloud HypervisorとNVXマイクロVMへの対応が加わった。利用できるプランはGitHub Free、Team、Enterpriseで、GitHub Copilot CLIエンジンを使う場合はCopilotライセンスが別途必要になる。導入企業の例としてAccentureが挙げられており、リーダー層で週29時間の業務削減、チーム全体では生産性が2倍以上に向上したという実績が紹介されている。

## 今後の展望

GitHub NextのプロジェクトがプレビューからGAに移行したことは、GitHub ActionsのワークフローにAIエージェントを組み込む開発スタイルが実運用レベルに達したことを示している。Markdownでワークフローを宣言的に書けるという手軽さと、サンドボックス化やファイアウォールといった防御機構を両立させている点が特徴で、今後は対応モデルやテンプレートの拡充、エンタープライズ向けのガバナンス機能の強化が進むと見られる。
