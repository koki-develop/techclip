---
date: "2026-04-11T10:38:06+09:00"
title: "Chrome 147がWebMLのクリティカル脆弱性2件を含む60件のセキュリティ修正をリリース"
description: "GoogleはChrome 147でヒープバッファオーバーフローと整数オーバーフローのクリティカル脆弱性2件を含む計60件のセキュリティ脆弱性を修正し、ユーザーへ即時アップデートを推奨している。"
tags:
  - Security
references:
  - "https://www.pcworld.com/article/3110607/chrome-147-patch-fixes-60-security-flaws-including-2-critical-ones.html"
  - "https://www.heise.de/en/news/Google-Chrome-147-Update-closes-60-security-vulnerabilities-two-critical-11249815.html"
  - "https://cybersecuritynews.com/chrome-vulnerabilities-patched/"
---

## 概要

Googleは2026年4月9日、Chrome 147の安定版をリリースし、合計60件のセキュリティ脆弱性を修正した。なかでも深刻度「Critical」に分類される2件の脆弱性は、いずれもWebMLコンポーネントに存在し、悪意を持って作成されたWebページを閲覧するだけでリモートコード実行が可能になるリスクがある。現時点ではこれらの脆弱性がインターネット上で実際に悪用された報告はないが、GoogleはChromeの即時更新を強く推奨している。

## クリティカル脆弱性の詳細

2件のクリティカル脆弱性はいずれもWebMLコンポーネントに起因する。

- **CVE-2026-5858**：WebMLにおけるヒープベースのバッファオーバーフロー。細工されたHTMLページを経由して任意のコードを注入・実行できる可能性がある。
- **CVE-2026-5859**：WebMLにおける整数オーバーフロー。同様に悪意あるコンテンツを通じた任意コード実行につながる恐れがある。

Googleはこれら2件の脆弱性を発見・報告した研究者それぞれに43,000ドルのバグバウンティ報奨金を支払っており、今回のアップデート全体での報奨金総額は118,000ドルに上る。残る58件の脆弱性は、高リスク14件（バッファオーバーフロー、use-after-freeなど）、中リスク20件、低リスク24件に分類される。V8 JavaScriptエンジンには型混乱（type confusion）の脆弱性が2件含まれていた。

## 対象バージョンとアップデート方法

修正済みのバージョンは以下の通り。

| プラットフォーム | バージョン |
|---|---|
| Windows / macOS | 147.0.7727.55 / 56 |
| Linux | 147.0.7727.55 |
| Android | 147.0.7727.49 |

Chromeはバックグラウンドで自動更新されるが、メニューの「ヘルプ」→「Google Chromeについて」から現在のバージョンを確認し、手動で更新を適用することもできる。なお、Microsoft EdgeなどChromiumベースのブラウザも同様の脆弱性の影響を受ける可能性があり、各ベンダーのアップデートを確認することが推奨される。次期バージョンのChrome 148は2026年5月初頭にリリース予定とされている。
