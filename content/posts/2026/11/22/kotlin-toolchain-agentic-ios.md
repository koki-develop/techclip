---
date: "2026-11-22T18:08:34+09:00"
title: "Kotlin Toolchain 0.14、「kotlin publish testflight」でiOS公開を一本化しAIエージェント対応も強化"
description: "JetBrainsがKotlin Toolchain 0.14をリリースし、iOSアプリをTestFlightへ公開するコマンドの簡素化とAIコーディングエージェント向けの支援機能を追加した。"
tags:
  - Programming Languages
references:
  - "https://blog.jetbrains.com/kotlin/2026/11/kotlin-toolchain-0-14-agentic-development-and-ios-publishing/"
---

## 概要

JetBrainsは11月17日、Kotlin Multiplatform向けビルドツール「Kotlin Toolchain」のバージョン0.14を公開した。今回の更新の柱は大きく2つで、iOSアプリの公開フローを大幅に簡素化したことと、AIコーディングエージェントによる開発を支援する新機能を追加したことだ。Kotlin Toolchainはコマンドライン主導でKotlin Multiplatformプロジェクトの作成・ビルド・パッケージングを担うツールであり、今回のリリースはモバイル配布とAI支援開発という2つの開発体験の改善に焦点を当てている。

## iOSアプリ公開の一本化

従来、Kotlin ToolchainでビルドしたiOSアプリをApp Store Connect経由でTestFlightに配布するには、`kotlin package --format=ipa`で署名済みの`.ipa`を生成した後、Xcodeプロジェクト側で開発チームや署名スタイル（自動・手動）を設定し、別途アップロード作業を行う必要があった。0.14では新コマンド`kotlin publish testflight`が追加され、初回公開に必要なセットアップから公開作業までを対話形式でガイドする一連のフローにまとめられた。コマンド実行時にApp Store Connectのアクセストークンの入力を求められる点は変わらず、Apple Developer Programへの加入は依然として前提となる。初回公開が完了すれば、以降のアップデートも同じコマンドで自動的に配布できるようになり、CI組み込みも容易になる。なお、手動署名など高度な設定が必要な場合は、引き続きXcodeプロジェクトを直接操作する従来の経路も利用可能だ。

## AIエージェント向けの支援機能

もう一つの大きな変更が、AIコーディングエージェントとの連携強化だ。Kotlin CLIのセットアップウィザードに、MCPサーバー設定やAGENTS.mdファイルをプロジェクトに自動生成する機能が追加された。AGENTS.mdはエージェントがプロジェクトの構造やビルド手順をより正確に把握し、試行錯誤による開発フィードバックループを短縮するための一般的な指針を記述するものだ。これに加えて、JetBrainsは「Kotlin agent skills collection」の一部としてKotlin Toolchain向けのスキルを公開しており、`npx skills add kotlin/kotlin-agent-skills`でインストールできる。これらはClaude CodeなどのAIエージェントがKotlin Toolchainベースのプロジェクトで作業する際の手順をMarkdown形式で教える仕組みで、JetBrainsのAI評価によればトークン消費量の削減にも寄与するという。

## その他の改善と今後の展望

0.14ではAndroid対応も拡充され、`module.yaml`に`desugaring: enabled`の一行を加えるだけでJava 8以降のAPIのdesugaringをネイティブに有効化できるようになった。desugaringライブラリ自体も`library`オプションで差し替え可能だ。また、Android依存関係のrelease/debugバリアント選択にも対応し、ビルド構成の柔軟性が向上した。パフォーマンス面では、キャッシュなしでKotlin Toolchain自身のプロジェクトをインポートする速度がベンチマークで3倍以上高速化したとしている。さらに、ツールチェーンが内部でダウンロードする外部ツールの取得元がすべて文書化され、環境変数での上書きにも対応した。iOS公開の簡素化とAIエージェント対応という2軸の改善は、Kotlin Multiplatformを「モバイル配布とAI支援開発の両面で扱いやすいプラットフォームにする」というJetBrainsの方向性を示しており、今後のバージョンでも両分野の機能拡充が続くと見られる。
