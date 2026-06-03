---
date: "2026-06-04T03:30:34+09:00"
title: "Google I/O 2026：ChromeがAIエージェント時代の「Agentic Web」に向けWebMCPなど15の新機能を発表"
description: "Google I/O 2026でChromeチームがAIエージェントとウェブを統合するオープン標準「WebMCP」を含む15件の開発者向けアップデートを発表し、ブラウザがAIエージェントをネイティブに扱える「Agentic Web」への移行を宣言した。"
tags:
  - Programming Languages
  - AI
references:
  - "https://developer.chrome.com/blog/chrome-at-io26"
  - "https://sdtimes.com/ai/google-i-o-2026-introduces-the-agentic-web-era-with-major-chrome-updates/"
  - "https://thenewstack.io/google-agent-ready-web/"
---

## 概要

Google I/O 2026において、ChromeチームはAIエージェントによる操作を前提とした新時代「Agentic Web」の到来を宣言し、開発者向けに15件のアップデートを発表した。中心となるのはオープンウェブ標準「WebMCP」で、Chrome 149でオリジントライアルが開始される。WebMCPはJavaScript関数やHTMLフォームなどの構造化ツールをブラウザエージェントに対して公開できる仕組みであり、「エージェントが機械向けの関数を呼び出して、複雑なタスクを数秒でより高い信頼性をもって実行できる」ことを可能にする。たとえば旅行の予約をユーザーが手動でフォームを埋めることなく自動化するといったシナリオが実現する。今回のアップデートは、ウェブを「ユーザーが操作するもの」から「エージェントがプロアクティブに動くもの」へと転換させる方向性を明確に示している。

## AIエージェント向け主要機能

**WebMCP**はAIエージェントとウェブサイトをつなぐ最重要機能で、サイト側がJavaScript関数やHTMLフォームを「エージェントフレンドリー」なAPIとして公開できるようにする。Chrome 149でオリジントライアルが始まり、Model Context Protocol（MCP）のウェブ版として位置付けられる。

**Chrome DevTools for Agents**（Update 3）ではエージェントがDevToolsのコンソールログやアクセシビリティツリーに直接アクセスできるようになる。LY Corporationはこの機能を活用して手動によるパフォーマンス分析作業を96〜98%削減したと報告している。

**Modern Web Guidance**（Update 2）はコーディングエージェント向けのガイドで、100以上のユースケースをカバーし、ブラウザ互換性指標「Baseline」と統合されている。開発者はモダンで安全かつ高パフォーマンスなウェブ体験を、手動でのフォールバック管理なしに構築できる。

## UI・パフォーマンス・ビルトインAI

**HTML-in-Canvas API**（Update 6）は、WebGL/WebGPUのCanvas内に実際のDOM要素を統合する技術で、3Dエクスペリエンスを検索可能・アクセシブル・ネイティブ翻訳対応のまま実現できる。**Declarative Partial Updates**（Update 7）はシングルページアプリケーション向けにネイティブな部分更新を提供し、複雑なDOM操作を不要にする。**Soft Navigations API**はSPAでCore Web Vitalsを計測するための標準として追加された。

**Built-in AI**（Update 5）では、Prompt APIがChrome 148で安定版となり、デバイス上で動作する超軽量モデル「Gemma 197M」も利用可能になった。Gemma 197Mはサーバーコストなしで無制限のリクエストを処理できる点が評価されており、Trip.comはローカルAIサマリーによりサーバー費用を削減している。

## Gemini統合とユーザー向け機能

Chromeに直接統合されるGemini機能も複数発表された。**Android向けGemini統合**（Update 10）は2026年6月から提供開始予定で、記事の要約やコンテキスト質問、カレンダー・Gmail・Keepとの連携ができる。**Auto Browse**（Update 11）はパーキングの予約などのタスクをAIエージェントが自動化する機能でAndroidとデスクトップの両方で動作する。**Skills in Chrome**（Update 13）は頻繁に使うAIプロンプトをワンクリックツールとして保存・再利用できる機能だ。また、**音声インタラクション**（Update 15）ではGeminiモデルを用いた文字起こし補正付きの音声フォーム入力が可能になる。

## 今後の展望

Expedia、Booking.com、Shopify、Trip.comといった主要企業がすでにこれらの技術を試験運用しており、ウェブのエージェント対応が加速している。Googleは今回の発表を通じて、ブラウザを「ユーザーが全力で操作しなければならないもの」から「ウェブがプロアクティブにユーザーのために動くもの」へと変えるビジョンを明示した。WebMCPをはじめとするオープン標準化への取り組みは、特定ベンダーに依存しないエージェント対応ウェブの基盤づくりに向けた重要な一歩として注目される。
