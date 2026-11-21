---
date: "2026-11-21T18:08:16+09:00"
title: "GitHub Copilot、Claude Opus 4.8/5とGPT-5.6 Terraを非推奨化 Opus 5.5やGPT-6.1 Solへ移行を推奨"
description: "GitHubが2026年11月16日、Copilotで利用可能なモデルのうちClaude Opus 4.8/5とGPT-5.6 Terraを非推奨化し、新モデルへの移行を促した。"
tags:
  - AI
  - OSS
references:
  - "https://github.blog/changelog/2026-11-16-github-copilot-models-deprecated-on-november-16-2026/"
---

## 概要

GitHubは11月16日、GitHub Copilotで提供していたモデルのうちClaude Opus 4.8、Claude Opus 5、GPT-5.6 Terraの3モデルを非推奨化したと発表した。対象となるのはCopilot Chat、インラインエディット、質問機能、エージェントモード、コード補完を含むほとんどのCopilot体験で、これらのモデルを指定して利用していた開発者は設定の見直しが必要になる。

## 推奨される移行先

GitHubは非推奨化したモデルに対応する移行先として、Claude Opus 4.8およびClaude Opus 5の利用者にはClaude Opus 5.5を、GPT-5.6 Terraの利用者にはGPT-6.1 SolまたはGPT-6 Lunaを推奨している。Copilot EnterpriseおよびBusinessの顧客については、デフォルト設定のままであれば自動的に代替モデルへ切り替わるため、追加の作業は基本的に不要となる。一方、モデルを明示的に指定したワークフローや統合を組んでいる場合は、サポート対象モデルへの更新が求められる。

なお、年間契約を結んでいる個人向けCopilot購読者に限り、Claude Opus 4.8は非推奨化後も継続して利用できる特例が設けられている。

## 影響と今後の対応

Copilotは短い周期で新モデルを追加・入れ替えており、今回のように旧モデルが比較的早いタイミングで非推奨化されるケースが続いている。CIやエディタ拡張、社内ツールなど特定モデルIDをハードコードして利用しているケースでは、非推奨化のタイミングで呼び出しが失敗する可能性があるため、開発チームは利用中のモデル名を棚卸しし、サポート対象モデルへの切り替えを計画的に進める必要がある。
