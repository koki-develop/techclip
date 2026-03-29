---
date: "2026-03-30"
title: "Google、Chromeで悪用確認済みのゼロデイ2件を緊急修正 ― SkiaとV8に深刻な脆弱性"
description: "GoogleがChromeのSkiaグラフィックライブラリとV8エンジンに存在した高深刻度のゼロデイ脆弱性2件（CVE-2026-3909・CVE-2026-3910）を修正し、即時アップデートを呼びかけている。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/03/google-fixes-two-chrome-zero-days.html"
  - "https://www.bleepingcomputer.com/news/google/google-fixes-two-new-chrome-zero-days-exploited-in-attacks/"
---

## 概要

Googleは2026年3月、Chrome安定版をバージョン146.0.7680.75/.76へ更新し、実際の攻撃で悪用が確認されていた2件のゼロデイ脆弱性を修正した。いずれもCVSSスコア8.8の高深刻度と評価されており、Googleは「CVE-2026-3909およびCVE-2026-3910のエクスプロイトが野外に存在する」と確認している。修正版はWindows（146.0.7680.75）、macOS（146.0.7680.76）、Linux（146.0.7680.75）向けに提供されている。

## 脆弱性の技術的詳細

1件目の**CVE-2026-3909**は、Chromeが描画処理に使用する2DグラフィックライブラリSkiaにおける境界外書き込み（out-of-bounds write）の脆弱性である。細工されたHTMLページを通じて境界外メモリアクセスが可能となり、ブラウザのクラッシュやコード実行につながる恐れがある。

2件目の**CVE-2026-3910**は、V8 JavaScriptおよびWebAssemblyエンジンにおける不適切な実装（inappropriate implementation）の脆弱性で、細工されたHTMLページを介してサンドボックス内での任意コード実行を許す可能性がある。

両脆弱性ともGoogle内部で発見され、3月10日に検出、3月13日に情報が公開された。Googleはパッチの普及を優先するため、脆弱性の詳細な技術情報やエクスプロイトの手法については「ユーザーの大多数がアップデートを適用するまで制限する」方針をとっている。

## 2026年のChromeゼロデイ動向と対応状況

今回の修正により、2026年に入ってからGoogleが対処したChromeの悪用済みゼロデイは合計3件となった。2月にはCSSFontFeatureValuesMapにおけるイテレータ無効化に起因するuse-after-freeの脆弱性（CVE-2026-2441、CVSS 8.8）が修正されている。なお、2025年通年ではChromeのゼロデイは8件が修正されており、2026年は3か月で既にその約4割に達するペースとなっている。

米国サイバーセキュリティ・インフラセキュリティ庁（CISA）は3月13日、両脆弱性を既知の悪用済み脆弱性カタログ（KEV）に追加し、連邦文民行政機関（FCEB）に対して3月27日までの修正適用を義務付けた。一般ユーザーもChromeの「ヘルプ > Google Chromeについて」から最新版への更新を速やかに行うことが強く推奨される。
