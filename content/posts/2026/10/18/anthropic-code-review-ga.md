---
date: "2026-10-18T18:12:04+09:00"
title: "Claude Codeの「Code Review」が正式提供開始、レビュー時間を1/3に短縮しEnterpriseには最大5万ドルのクレジット"
description: "AnthropicはClaude Code向けのPRレビュー機能「Code Review」をリサーチプレビューから正式提供に移行し、レビュー速度の高速化とEnterprise向けクレジットを発表した。"
tags:
  - AI
  - OSS
references:
  - "https://claude.com/resources/articles/code-review-is-now-generally-available"
  - "https://thenextweb.com/news/anthropic-code-review-ga-eu-residency"
  - "https://www.unite.ai/anthropic-makes-code-review-for-claude-code-generally-available/"
---

## 概要

Anthropicは10月15日、Claude CodeのPull Requestレビュー機能「Code Review」をリサーチプレビューから正式提供（GA）へ移行し、Team・Enterpriseプランの顧客に提供を開始した。最大の変化はレビュー時間の短縮で、プレビュー期間の約20分から6〜10分へと、およそ3倍の高速化を実現したとしている。併せて、誤検知の低減や指摘内容の質も改善されており、各指摘は「問題点・発生条件・修正方法」を明示する簡潔な形式で提示される。

## レビュー強度の選択とアーキテクチャ

管理者はリポジトリ単位でレビューの強度を3段階から選択できるようになった。日常的なコードベース向けの「Quick」、標準的な審査を行う「Standard」（デフォルト）、そして最も重要なリポジトリ向けに徹底した検証を行う「Deep」である。処理は4段階のパイプラインで構成され、複数のエージェントが並行して問題を検出し、誤検知をフィルタリングした上で重複を排除・重大度でランク付けし、最終的にPull Requestへ結果を投稿する仕組みになっている。unite.aiの報道によれば、こうした改善を通じて実質的なコメント率は16%から54%へ増加したという。利用にはGitHubアプリのインストールとリポジトリごとの指定が必要で、対応はGitHub上のリポジトリ（GitHub Enterprise含む）に限られる。

## Enterprise向けクレジットと適用除外

Claude Enterpriseの顧客は、GA移行を記念してアクティブシート数に応じ1万ドルから5万ドルのCode Reviewクレジットを申請できる。申請期限は2027年1月15日で、付与されたクレジットは申請から30日で失効する点に注意が必要だ。一方で、GitHub Enterprise Cloudでデータレジデンシー設定（`.ghe.com`アドレス）を利用している組織はこのプロモーションの対象外となる。The Next Webの報道では、該当設定を行った状態で接続すると、github.com上のレビュー分も含め組織全体のクレジットが停止すると指摘されている（レビュー機能自体は有償で引き続き利用できる）。また、HIPAA設定やゼロデータ保持を有効にしている組織では、Code Review自体が利用できない。

## 背景と今後の展望

Code Reviewは今年6月、Claude Code Action経由でのプロンプトインジェクション脆弱性が研究者から報告され、Anthropicは4日で対応し4,800ドルの報奨金を支払った経緯がある。GA移行はこうした安全性対応を経た上での一般提供拡大という位置づけだ。市場ではCodeRabbitが週200万件のレビュー・17,000の顧客基盤を背景に欧州展開を加速させるなど、AIによるコードレビュー領域の競争が激化している。The Next Webは、リサーチプレビュー期間のレビュー原価が1件あたり15〜25ドルだったと報じており、GA後の正式な価格体系がどうなるかは現時点では明らかにされていない。製品の注記にも「AIであり、バグを見落とす可能性がある」とある通り、自動レビューを過信せず人間によるレビューと組み合わせて運用することが推奨される。
