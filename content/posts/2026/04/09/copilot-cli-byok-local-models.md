---
date: "2026-04-09T10:38:48+09:00"
title: "GitHub Copilot CLIがBYOK・ローカルモデル対応、エアギャップ環境での利用も可能に"
description: "GitHub Copilot CLIがOpenAI・Anthropic・Azure OpenAI互換エンドポイントやOllama・vLLMなどのローカルモデルに対応し、オフラインモードでのエアギャップ環境での動作も可能になった。"
tags:
  - OSS
references:
  - "https://github.blog/changelog/2026-04-07-copilot-cli-now-supports-byok-and-local-models/"
---

## 概要

GitHub Copilot CLIは2026年4月7日、独自のモデルプロバイダーやローカルモデルの利用に対応したことを発表した。これまではGitHubのホストモデルルーティングに限定されていたが、今回のアップデートにより、ユーザーは環境変数を設定するだけで、OpenAI・Azure OpenAI・Anthropicなどのリモートサービスや、OllamaやvLLM、Foundry Localといったローカルモデルを接続して利用できるようになった。

オフラインモードとして `COPILOT_OFFLINE=true` を設定すると、GitHubのサーバーへの通信が遮断され、テレメトリも無効化される。このモードとローカルモデルを組み合わせることで、インターネット接続のないエアギャップ環境や厳格なセキュリティポリシーが求められる企業・政府機関などの開発環境でも、Copilot CLIを活用できるようになる。

## 技術的な詳細

カスタムモデルプロバイダーを使用する際には、GitHub認証は必須ではない。ただし、GitHubアカウントにサインインすることで、`/delegate` コマンドやGitHub Code Searchといった追加機能にもアクセスできる。対応するモデルの条件として、ツール呼び出し（function calling）とストリーミングのサポートが必要であり、最低128kトークンのコンテキストウィンドウを持つモデルが推奨される。

サブエージェント機能（explore・task・code-review）は、設定されたプロバイダー情報を自動的に継承する。なお、設定が無効な場合でもGitHubホストモデルへの自動フォールバックは行われず、エラーメッセージが表示される仕様となっている。セットアップ手順は `copilot help providers` コマンドで確認できる。

## 意義と展望

このBYOK（Bring Your Own Key）対応は、コンプライアンスやデータプライバシーの観点からGitHubの標準モデルを利用できなかった組織にとって大きな選択肢の拡大となる。特に、閉鎖的なネットワーク環境での開発を余儀なくされるケースでも、AI支援の恩恵を受けられるようになる点で意義深い。また、ローカルLLMの多様な選択肢を活用できるようになることで、コストやレイテンシの観点でも柔軟な運用が可能になる。
