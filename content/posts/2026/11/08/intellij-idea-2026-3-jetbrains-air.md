---
date: "2026-11-08T18:07:42+09:00"
title: "JetBrains、エージェント型開発基盤「JetBrains Air」とJava 28対応を備えた「IntelliJ IDEA 2026.3」をリリース"
description: "JetBrainsがIntelliJ IDEA 2026.3を公開し、エージェント型開発基盤「JetBrains Air」、Java 28対応、Git worktreesサポートを追加した。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://www.jetbrains.com/help/idea/new-in-this-release.html"
  - "https://vinish.dev/intellij-idea-2026-3-released-air-java-28-git-worktrees"
---

## 概要

JetBrainsは11月5日、Java/Kotlin向けIDE「IntelliJ IDEA」の最新版2026.3をリリースした。今回の目玉は、エージェント型開発を担う新プラットフォーム「JetBrains Air」の投入だ。これはIntelliJ IDEAの上に新設されたエージェント体験の層で、CursorやVS Code向けの拡張機能としても提供され、IntelliJ IDEAが持つJavaおよびKotlinの言語理解機能を、これらの他社製エディタ上でも利用できるようにする。JetBrains AirはまずEAP（早期アクセスプログラム）として公開されており、AIコーディングエージェントとの統合(ACP)やAgent Skillsといった機能群がその土台となる。

言語・ツールチェーン面では、Java 28への対応が加わり、Jakarta Persistence 4およびHibernate 8もサポートされた。Project Loomによる仮想スレッド、スコープ値、構造化並行処理への対応も進み、仮想スレッドに対応したスレッドダンプ表示機能が追加されている。

## 新機能の詳細

開発者から最も要望が多かった機能のひとつとして、Git worktreesのサポートが実装された。マルチルートプロジェクトでの利用に対応し、別のworktree上でマージリクエストを開く操作も可能になった。バージョン管理周りでは、ハードウェアトークン（YubiKeyなど）に対応するためOpenSSHの採用も進められている。

その他、テストカバレッジ計測の既定ランナーがJaCoCoに切り替わり、Spring Data向けのリポジトリメソッド補完が再設計された。WSL環境のサポートも進化し、コンパクトオブジェクトヘッダーやログポイントなど、デバッグ・診断系の機能強化も盛り込まれている。

## 安定性とパフォーマンスの改善

今回のリリースでは1,000件を超えるバグ修正と300件以上のパフォーマンス改善が行われた。改善の中心はフリーズの解消、CPU使用率の低減、メモリ管理の最適化で、Spring Bootのinlay hints表示や大規模なGradle/Mavenプロジェクトのインポート処理など、日常的な開発体験に直結する部分が最適化されている。

エージェント型開発への対応を本体の外側にレイヤーとして切り出しつつ、言語サポートと基盤の安定性を同時に強化した点が今回のリリースの特徴といえる。JetBrains Airが今後どこまで独立した製品として展開されるか、エディタを問わない横断的なツールとしての立ち位置も含めて注目される。
