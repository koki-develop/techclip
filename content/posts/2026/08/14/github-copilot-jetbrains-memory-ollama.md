---
date: "2026-08-14T20:14:13+09:00"
title: "GitHub Copilot for JetBrainsが会話メモリとOllama連携に対応、セッションを超えた文脈保持とローカルモデル利用が可能に"
description: "GitHub Copilot for JetBrainsに、セッションをまたいで文脈を保持するCopilot memory機能と、ローカルモデルをBYOKで利用できるOllama連携が追加された。"
tags:
  - OSS
  - AI
references:
  - "https://github.blog/changelog/2026-08-11-copilot-memory-and-ollama-in-github-copilot-for-jetbrains/"
---

## 概要

GitHubは8月11日、JetBrains向けGitHub Copilotに2つの新機能を追加したと発表した。1つ目は「Copilot memory」と呼ばれる会話メモリ機能で、agent chatのセッションをまたいで有用な情報を保持・想起できるようになる。プロジェクトの詳細や個人の設定を毎回入力し直す手間がなくなり、開発者はより自然な形でCopilotとの対話を継続できる。2つ目は、ローカルモデルプロバイダーとしてOllamaをBYOK(Bring Your Own Key/Model)方式で選択できる連携機能で、開発者はクラウドサービスに依存せずローカル環境で動くモデルを使ったコーディング支援を受けられるようになった。

## 機能の詳細

Copilot memoryは、Copilot設定ポータル内の「Copilot Memory」トグルで有効・無効を切り替えられる。有効にすることで、これまでチャットセッションごとにリセットされていた文脈情報がセッションを越えて保持され、プロジェクト固有の情報や開発者ごとの好みを繰り返し伝える必要がなくなる。一方のOllama連携は、JetBrainsのプロバイダー設定・モデル選択のUI全体に統合されており、他のBYOKプロバイダーと同様の操作感でローカルモデルを組み込める設計になっている。今回のアップデートにはCopilot CLIの自動インストール対応も含まれており、macOS・Linux・Windowsの各プラットフォームで利用可能とされている。

## 背景と今後

ローカルLLMを手軽に実行できるOllamaとの連携は、機密性の高いコードをクラウドに送信したくない開発者や、オフライン環境での開発を求めるユーザーにとって有力な選択肢となる。GitHubは今回の変更点についてフィードバックを募集しており、JetBrains版Copilotの機能拡張は今後も継続していく方針とみられる。会話メモリ機能とあわせて、Copilotの利用体験は「その場限りのアシスタント」から「開発者の文脈を学習し続けるパートナー」へと進化を続けている。
