---
date: "2026-04-29T02:38:13+09:00"
title: "IntelliJ IDEA 2026.1.1リリース：WSL・Gradle・リモート開発の不具合を修正"
description: "JetBrainsがIntelliJ IDEA 2026.1.1をリリースし、WSL Python SDK設定やGradleの同期クラッシュ、リモート開発のEmmetサポートなど複数のバグを修正した。"
tags:
  - Programming Languages
references:
  - "https://blog.jetbrains.com/idea/2026/04/intellij-idea-2026-1-1/"
---

## 概要

JetBrainsは2026年4月23日、IntelliJ IDEA 2026.1.1をリリースした。本バージョンは新機能の追加ではなく、2026.1系における安定性向上とバグ修正に特化したメンテナンスリリースである。WSL（Windows Subsystem for Linux）環境でのPython SDK設定、リモート開発のEmmetサポート、Gradleの同期クラッシュなど、多くの開発者が直面していた問題が解消されている。アップデートはIDE組み込みの更新機能、Toolbox App、Ubuntu Snap、またはJetBrainsの公式サイトからのダウンロードで適用できる。

## 主な修正内容

開発環境に関連する修正として、WSL上でのPython SDK設定が再び正常に動作するようになった。加えて、WSL 2上にインストールされたJDKをIDEが正しく検出できるようになり、WSLを活用したJava開発のセットアップが改善されている。リモート開発環境ではEmmetのサポートが修正され、HTMLやCSSのコード展開が正常に機能するようになった。

ビルドツールとデプロイ周りでは、`InternalIdeaModule`のクラスキャスト問題に起因するGradleの同期クラッシュが修正された。また、WildFlyの管理プロセスへの接続が復元され、デプロイ操作やブラウザ起動オプションが利用可能になった。WebLogicの実行構成の作成も正常化されている。

## その他の改善点

Antツールウィンドウでターゲットをダブルクリックした際にビルドが実行されてビルド出力が正しく表示されるよう修正された。「検索と置換」機能でEnterキーが正常に動作するようになったほか、Springプロジェクトにおけるコンテキストアクションの検索とコード補完の応答速度が向上している。特に大規模なSpringプロジェクトでは、検索や補完機能において顕著なパフォーマンス改善が見られるとJetBrainsは報告している。

