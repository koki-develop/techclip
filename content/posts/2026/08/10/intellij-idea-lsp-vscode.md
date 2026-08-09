---
date: "2026-08-10T08:06:00+09:00"
title: "JetBrains、IntelliJ IDEAのJava/Kotlin解析エンジンをLSP拡張機能としてVS Code・Cursorに開放"
description: "JetBrainsがIntelliJ IDEAのJava/Kotlin言語解析機能をLanguage Server Protocol経由でVS CodeやCursorなどのエディタに提供するプレビュー版拡張機能を公開した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://blog.jetbrains.com/idea/2026/08/intellij-idea-goes-lsp/"
---

## 概要

JetBrainsは8月4日、IntelliJ IDEAが持つJavaおよびKotlinの言語解析エンジンをLanguage Server Protocol(LSP)経由で外部エディタに提供するプレビュー版拡張機能「Java & Kotlin by IntelliJ IDEA」を公開した。これにより、VS CodeやCursorといったIntelliJ IDEA以外のエディタでも、同IDEが培ってきた高精度なコード解析やリファクタリング機能を利用できるようになる。拡張機能はVisual Studio MarketplaceおよびOpen VSXレジストリから入手可能で、Maven・Gradle・Bazelでビルドされたプロジェクトや、Java/Kotlin混在プロジェクトに対応する。

## 技術的な詳細

拡張機能はLSPを介してIntelliJ IDEAのバックエンド解析エンジンをそのまま呼び出す構成で、スマートなコード補完、シンボルナビゲーション、コード解析、リファクタリング、エディタ支援に加え、Debug Adapter Protocol(DAP)ベースのデバッグ機能も備える。プレビュー期間中は無料で利用できるが30日間の評価期間制限が設けられており、正式版としての継続利用にはIntelliJ IDEA Ultimateのサブスクリプションが必要になる見込みだ。

## 背景と狙い

これまでIntelliJ IDEAの強力な言語解析はJetBrains製IDE内に閉じた機能であり、VS CodeやCursorのユーザーはTypeScriptベースの軽量な言語サーバーに頼らざるを得なかった。今回のLSP対応は、エディタの選択によらずJetBrainsの解析エンジンを利用可能にすることで、この差を埋める狙いがある。特にAIコーディングエージェントが多くの実装作業を担うようになり開発者自身が手作業でコードを編集する機会が減る中、エージェントが参照する解析結果がより高速かつ決定論的になることで、無駄なトークン消費を抑えられる点をJetBrainsは利点として挙げている。

## 今後の展望

JetBrainsはターミナルベースのエージェント型ワークフローへの対応も実験的に進めており、近く有望な結果を公開する予定だとしている。VS CodeやCursorのようなエディタ上でAIエージェントによる開発が一般化しつつある中、IntelliJ IDEA由来の高精度な言語解析がエージェントの精度向上にどう寄与するかが今後の焦点となりそうだ。
