---
date: "2026-04-15T02:32:48+09:00"
title: "Next.js v16.2.3リリース、React Server ComponentsのDoS脆弱性CVE-2026-23869を修正"
description: "Next.js v16.2.3がリリースされ、App RouterのServer FunctionエンドポイントにおけるDoS脆弱性（CVE-2026-23869、CVSS 7.5）へのセキュリティ修正を含む複数のバグ修正がバックポートされた。"
tags:
  - Programming Languages
  - Security
references:
  - "https://github.com/vercel/next.js/releases/tag/v16.2.3"
  - "https://vercel.com/changelog/summary-of-cve-2026-23869"
---

## 概要

Vercelは2026年4月8日、Next.js v16.2.3をリリースした。本リリースはセキュリティ修正とバグ修正のバックポートに特化したもので、カナリアブランチの新機能は含まない。最大の変更点は、React Server ComponentsのApp RouterにおけるDoS脆弱性（CVE-2026-23869）の修正であり、Next.js 13.x〜16.xを利用するプロジェクトのすぐさまアップグレードが推奨されている。

## CVE-2026-23869の詳細

CVE-2026-23869はCVSSスコア7.5（高）と評価されたDoS（Denial of Service）脆弱性で、App RouterのServer Functionエンドポイントに影響する。攻撃者が特定の細工を施したHTTPリクエストをServer Functionエンドポイントへ送信すると、デシリアライズ処理中にCPUを過剰消費させることができ、正規ユーザーへのサービス停止を引き起こす可能性がある。

影響を受けるバージョンはNext.js 13.x・14.x・15.x・16.xと広範で、修正済みバージョンはNext.js 15.5.15以降および16.2.3以降となる。Vercelのホスティング環境ではWAF（Webアプリケーションファイアウォール）ルールによる自動保護も実施されているが、公式アドバイザリはプラットフォーム側の保護のみに依存せず、パッチ済みバージョンへの即時アップグレードを強く求めている。

## その他のバグ修正

セキュリティ修正に加え、v16.2.3では以下の不具合も修正されている。

- **ISRエラー報告の修正**: `onRequestError`を通じてアプリページが古いISR再検証エラーを正しく報告するよう改善された。
- **HMRの不具合修正**: Next.js 16.2で発生していた`manifest.ts`が原因のHMR（Hot Module Replacement）停止バグが解消された。
- **出力アセットの重複排除**: ビルド時の出力アセットの重複を排除し、コンテンツ競合を検出する仕組みが追加された。
- **styled-jsxの競合状態修正**: 並行レンダリング時にスタイルが失われる競合状態が修正された。
- **turbo-tasks-backendの安定性向上**: タスクキャンセルおよびエラーハンドリングに関する安定性修正が含まれる。

## 対応のポイント

App Routerを使用しているすべてのNext.jsプロジェクトがCVE-2026-23869の影響範囲に入るため、早急なアップグレードが必要だ。Self-hosted環境ではVercelのWAF保護が適用されないため、特にバージョンアップが急務となる。v16.2.3への更新は`npm install next@16.2.3`または各パッケージマネージャーの相当コマンドで実施できる。
