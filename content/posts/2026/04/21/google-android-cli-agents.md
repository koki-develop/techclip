---
date: "2026-04-21T18:30:42+09:00"
title: "GoogleがAIエージェント向けAndroid CLIを発表——トークン使用量70%削減、開発速度3倍を実現"
description: "GoogleはAIエージェントによるAndroidアプリ開発を3倍高速化する新CLIツール「Android CLI」を発表し、LLMのトークン消費量を70%削減するとともに、Markdownベースのスキルモジュールで複雑なワークフローを自動化できる。"
tags:
  - OSS
  - AI
references:
  - "https://android-developers.googleblog.com/2026/04/build-android-apps-3x-faster-using-any-agent.html"
  - "https://www.theregister.com/2026/04/20/google_previews_android_cli"
---

## 概要

Googleは2026年4月、AIエージェントによるAndroidアプリ開発を抜本的に高速化することを目的とした新ツール群を発表した。中心となる「Android CLI」は、Android SDKへの軽量なプログラム的アクセスを提供するコマンドラインインターフェースで、内部テストによればLLMのトークン使用量を70%以上削減し、タスク完了速度を従来の3倍に向上させると報告されている。このツールはApple Silicon、AMD64 Linux、AMD64 Windowsに対応しており、d.android.com/tools/agentsから入手できる。

## 3つのコアコンポーネント

発表された新ツール群は3つの主要コンポーネントで構成される。

**Android CLI** は`android sdk install`（SDK管理）、`android create`（プロジェクト生成）、`android emulator`（デバイス管理）、`android run`（アプリデプロイ）、`android update`（更新）といったコマンドを通じて、エージェントがAndroid開発の主要操作を簡潔に実行できるよう設計されている。`android describe`引数でプロジェクトのメタデータを生成する機能も持つ。

**Android Skillsリポジトリ** は、Markdownベースの指示セット（`SKILL.md`）をエージェントに提供し、複雑なワークフローをベストプラクティスに沿って実行させる仕組みだ。`android skills`コマンドで呼び出せるスキルは、現時点でNavigation 3への移行、エッジtoエッジ対応の実装、AGP 9およびXMLからComposeへの移行、R8設定の分析など7種類が用意されている。

**Android Knowledge Base** は`android docs`コマンドでアクセスでき、Androidデベロッパードキュメント、Firebase、Google Developers、Kotlinドキュメントを横断して情報を検索・取得できる専用リソースだ。

## Android Studioとの関係と業界の動向

Android CLIはAndroid Studioを置き換えるものではなく、補完的な位置づけとされている。Googleは「CLIベースのエージェントで素早くプロトタイプを構築し、その後Android Studioでプロジェクトを開いてUIの仕上げや高度なデバッグ・プロファイリングを行う」という使い方を想定している。

一方、The Registerの報道では、現状のスキル数が7種類にとどまることや、ツールが「LLMがすでに得意な基本的なAndroidセットアップコマンドのラッパーに過ぎない」との開発者からの批判的な声も紹介されている。ただし、MicrosoftやJetBrainsも同様にエージェント向け開発ツールを整備しつつあり、従来の人間向けIDEをAI自律エージェントのワークフロー向けに再設計するという業界全体のトレンドの一環として捉えることができる。Android CLIが今後スキルや機能を拡充することで、Androidエージェント開発のデファクトスタンダードとなれるかが注目される。