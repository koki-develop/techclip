---
date: "2026-07-22T02:33:21+09:00"
title: "IntelliJ IDEA 2026.2リリース、GitHub Copilotをネイティブ統合しAI開発支援を強化"
description: "JetBrainsがIntelliJ IDEA 2026.2を公開し、GitHub CopilotのOOTB統合やカスタムエージェントスキル管理、logpointsデバッグ機能に加え、Java 27・Kotlin 2.4・TypeScript 7への対応を追加した。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://ubuntuhandbook.org/index.php/2026/07/intellij-idea-2026-2-released-with-native-github-copilot-integration/"
---

## 概要

JetBrainsは2026年7月17日、Java/Kotlin向けIDE「IntelliJ IDEA」の最新版となる2026.2を公開した。今回の目玉は「GitHub Copilot out-of-the-box」で、追加のプラグインインストールなしにAIチャットのエージェントピッカーから直接GitHub Copilotを呼び出せるようになった点だ。認証はGitHubアカウントを使ったOAuthで完結し、利用にはアクティブなGitHub Copilotのサブスクリプションが必要となる。これまでサードパーティ拡張機能として提供されていたCopilot連携がIDE本体に標準搭載されたことで、セットアップの手間なくAIコーディング支援を利用できる環境が整った。

## AIエージェント・デバッグ機能の強化

Copilot統合と並行して、IDEにはカスタムエージェントスキルを検出・インストール・管理する機能が組み込まれた。JetBrainsが提供する組み込みライブラリだけでなく、ローカルプロジェクトやGitHubリポジトリに存在するスキルも取り込めるようになり、開発者が自身のワークフローに合わせてAIエージェントの挙動を拡張しやすくなっている。デバッグ面では新機能「logpoints」が導入され、アプリケーションの実行を中断することなく内部状態を検査し、任意のカスタムメッセージを出力できるようになった。従来のブレークポイントによる実行停止を伴うデバッグに比べ、本番に近い環境でのトラブルシューティングがしやすくなる。

## 開発支援機能の改善

依存関係管理では、クラウドベースの検索機能によりビルドファイル内でライブラリ名を入力するだけでマッチする候補が表示されるようになり、依存関係の追加作業が簡素化された。またビルドツール面ではGradle 9.7以上との組み合わせでの同期がスムーズになるよう調整されており、今後リリースが予定されるGradle 10への対応準備も進められている。このほか、Git競合解決の自動化、Flyway・Liquibaseを用いたデータベースマイグレーションワークフローの改善、Spring Securityに関するインサイト表示の向上、Terraformテストフレームワークへのネイティブ対応など、開発ワークフロー全般にわたる改善が加えられている。

## 言語サポートの拡充

言語サポートも大きく強化された。Java 27に対応したほか、Kotlin 2.4.0の最新機能、TypeScript 7、Scala 3の新機能もサポート対象に加わった。AI機能とコア言語サポートの両輪で強化を図る姿勢は、JetBrainsが競合するAI搭載エディタやIDEに対して開発体験の完成度で対抗しようとしていることを示している。GitHub Copilotの標準搭載により、IntelliJ IDEAはAIコーディング支援ツールの選択肢を増やしつつ、既存のJetBrains AI Assistantと合わせて複数のAIエージェントを使い分けられる環境を提供する形となった。
