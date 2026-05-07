---
date: "2026-05-08T02:38:27+09:00"
title: "GitHub MCP ServerにシークレットスキャンがGA、依存関係スキャンもプレビュー公開"
description: "GitHub MCP Serverにコミット前の認証情報漏洩を検出するシークレットスキャン機能がGAとなり、同時にDependabotと連携する依存関係脆弱性スキャン機能がパブリックプレビューで公開された。"
tags:
  - OSS
  - Security
references:
  - "https://github.blog/changelog/2026-05-05-secret-scanning-with-github-mcp-server-is-now-generally-available/"
  - "https://github.blog/changelog/2026-05-05-dependency-scanning-with-github-mcp-server-is-in-public-preview/"
---

## 概要

GitHubは2026年5月5日、GitHub MCP（Model Context Protocol）Serverに2つのセキュリティスキャン機能を追加した。一つ目は、2026年3月のパブリックプレビューを経て正式GA（一般提供）となった**シークレットスキャン**機能で、コミットやPRを作成する前にコード内の認証情報・シークレットの漏洩をAIコーディングエージェントから直接検出できる。二つ目は、DependabotとGitHub Advisory Databaseを活用した**依存関係脆弱性スキャン**機能で、こちらはパブリックプレビューとして公開された。いずれもGitHub Copilot CLIおよびVisual Studio Code上のMCP互換ツールから利用可能だ。

## シークレットスキャン（GA）

シークレットスキャンは、開発者がAIエージェントに対して「現在の変更にシークレットが含まれていないかスキャンして」といった自然言語の指示を出すだけで実行できる。技術的には既存の「push protection customization」設定に準拠しており、リポジトリや組織レベルで設定したカスタマイズがそのまま反映される。利用にはGitHub Secret Protectionが有効なリポジトリが必要。

セットアップはGitHub Copilot CLIとVS Codeそれぞれで対応している。Copilot CLIでは`/plugin install advanced-security@copilot-plugins`でGitHub Advanced Securityプラグインを追加し、VS CodeではCopilot Chatのadvanced-securityエージェントプラグインをインストール後に`/secret-scanning`コマンドで利用できる。従来の事後的な検出から開発フローの早い段階での予防的アプローチへの転換を実現するものだ。

## 依存関係スキャン（パブリックプレビュー）

依存関係スキャンは`dependabot`ツールセットの一部として機能し、AIエージェントが変更した依存関係の情報をGitHub Advisory Databaseと照合することで、影響を受けるパッケージ・深刻度・推奨される修正バージョンを含む構造化された結果を返す。Dependabotアラートが有効なリポジトリで利用でき、ローカル環境でDependabot CLIを実行して変更前後の依存関係グラフを比較するより詳細な検証も可能だ。

Copilot CLIでは`copilot --add-github-mcp-toolset dependabot`コマンドで有効化でき、VS CodeではMCP Serverの設定ヘッダーに`"X-MCP-Toolsets": "dependabot"`を追加するか、Copilot Chatのツールセットセレクターから選択する。「このブランチで追加した依存関係に既知の脆弱性がないかスキャンして、コミット前にアップグレードすべきバージョンを教えて」といったプロンプトが推奨されている。

## セキュリティをAI開発フローに組み込む意義

これら2つの機能は、AIを活用したコーディング体験（IDE・CLIのエージェント）にセキュリティ検査をシームレスに統合するという方向性を示している。コードを書くAIエージェントが、書いたコードの安全性も同時に検査できる環境を整えることで、シフトレフトセキュリティの実践をより低摩擦で実現することが狙いだ。GitHubはGitHub Advanced Securityプラグインの活用を推奨しており、今後もMCP Serverを通じたセキュリティ機能の拡充が期待される。
