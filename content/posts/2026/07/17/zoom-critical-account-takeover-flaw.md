---
date: "2026-07-17T02:33:10+09:00"
title: "Zoom Windows版に深刻な脆弱性CVE-2026-53412、CVSS9.8のアカウント乗っ取りリスクで緊急パッチ"
description: "Zoomがデスクトップクライアント（Windows版）などに存在する認証不要でアカウント乗っ取りが可能な重大脆弱性CVE-2026-53412（CVSS9.8）を含む複数の脆弱性を修正し、ユーザーに最新版への更新を呼びかけている。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/07/zoom-patches-critical-windows-flaw-that.html"
  - "https://www.bleepingcomputer.com/news/security/zoom-warns-of-critical-account-takeover-vulnerability/"
  - "https://securityaffairs.com/195454/security/zoom-fixes-cve-2026-53412-a-critical-account-takeover-bug.html"
---

## 概要

Zoomは、Windows版のデスクトップクライアントを中心に、認証なしでネットワーク経由の攻撃によりアカウントを乗っ取られる恐れのある重大な脆弱性「CVE-2026-53412」を修正したと発表した。CVSSスコアは最高水準に近い9.8と評価されており、脆弱性の原因は「不適切な入力値検証」とされている。攻撃者はログイン認証を経ることなく、ネットワークにアクセスできるだけでアカウントを乗っ取れる可能性があり、Zoomを業務コミュニケーションの基盤として利用する組織にとって深刻なリスクとなる。現時点では実際の攻撃（in-the-wild exploitation）は確認されていないが、Zoomはユーザーに対し速やかな更新を呼びかけている。

## 影響を受ける製品とバージョン

CVE-2026-53412の影響を受けるのは、Zoom Desktop Client for Windows、Zoom VDI Client for Windows、Zoom Meeting SDK for Windowsなど、Windows環境向けの主要クライアント群である。具体的には、Zoom Workplace for Windowsのバージョン7.0.0未満、Windows VDI Clientのバージョン7.0.10・6.6.15・6.5.18未満、Meeting SDK for Windowsのバージョン7.0.0未満が対象とされている。macOSやLinux版、モバイル版など他プラットフォームへの言及は各記事に見られず、今回の深刻な脆弱性はWindows環境に固有の問題である可能性が高い。

## 同時に修正された関連脆弱性

Zoomは今回のセキュリティアップデートで、CVE-2026-53412とあわせて3件の高危険度脆弱性も修正している。VDI Plugin 6.6.14以前に存在する認証ユーザーによる権限昇格の脆弱性（CVE-2026-53411）、インストールおよびアンインストール処理におけるTOCTOU（Time-of-Check to Time-of-Use）競合状態に起因する脆弱性（CVE-2026-53410、Workplace 7.0.5・VDI Client 6.5.17および6.6.14・Rooms 7.0.5以前が対象）、そしてZoom Rooms for Windows 7.1.0以前における権限管理の不備（CVE-2026-53409）である。報道によりCVSSスコアの表記に7点台とする記事と8.8とする記事があり、細部の評価には若干のばらつきが見られるが、いずれも高危険度に分類される点は共通している。

## 今後の対応

Zoomは脆弱性の技術的な詳細については公開しておらず、発見はZoomのセキュリティチーム自身によるものとされている。現時点で悪用の報告はないものの、CVSS9.8という数値が示す通り攻撃条件が緩く影響が大きいため、Windows版のZoomクライアントを利用している企業・個人は速やかに最新バージョンへアップデートすることが強く推奨される。特にVDI環境やMeeting SDKを組み込んだ独自アプリケーションを運用している組織は、依存コンポーネントのバージョンも含めて確認する必要がある。
