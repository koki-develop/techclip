---
date: "2026-11-10T18:09:28+09:00"
title: "Chromeに2026年8件目の悪用済みゼロデイ、XMLコンポーネントのUse-After-Freeを修正"
description: "GoogleはChrome 157.0.8103.50/.51をリリースし、実際に悪用されているXMLコンポーネントのUse-After-Free脆弱性CVE-2026-125350を含む9件の脆弱性を修正した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/11/google-issues-chrome-security-update.html"
  - "https://www.bleepingcomputer.com/news/security/google-patches-eighth-chrome-zero-day-exploited-in-attacks-this-year/"
  - "https://www.securityweek.com/chrome-update-patches-exploited-xml-zero-day-eighth-this-year/"
---

## 概要

Googleは11月10日、Chrome 157.0.8103.50/.51(Windows/macOS)および157.0.8103.50(Linux)をリリースし、合計9件の脆弱性を修正した。その中核は、XMLコンポーネントに存在するUse-After-Free脆弱性CVE-2026-125350で、Googleは「CVE-2026-125350を悪用するエクスプロイトが野放しで存在することを認識している」と月曜のアドバイザリで述べており、既に実際の攻撃で悪用されていることを確認している。本脆弱性は匿名の研究者により11月6日にGoogleへ報告され、4日後の11月10日に修正版が公開された。これは2026年にChromeで修正された悪用済みゼロデイとしては8件目にあたり、2月のCVE-2026-2441(CSSFontFeatureValuesMapのイテレータ無効化)、4月のCVE-2026-5281(WebGPUのDawnにおけるUse-After-Free)、6月のCVE-2026-11645(V8の境界外読み書き)などに続くものだ。

## 技術的な詳細

CVE-2026-125350は、ChromeのXMLパーサーがメモリからオブジェクトを削除する際に、関連するポインタを適切にクリアしないことに起因するUse-After-Free(解放済みメモリの使用)欠陥だ。攻撃者はこの不整合を利用してメモリレイアウトを操作し、ブラウザが解放済みのメモリ領域へアクセスした際にデータ破損、プログラムクラッシュ、あるいは任意コード実行を引き起こすことができる。深刻度はHighと評価されているが、CVSSスコアは公開されていない。Googleの通例に従い、具体的な攻撃手法の詳細は、大多数のユーザーが更新を適用するまで非公開とされる。サードパーティライブラリに起因し他プロジェクトにも影響する脆弱性の場合は、この非公開期間がさらに延長されることもあるという。なお、SecurityWeekによれば、記事執筆時点でCISAの既知の悪用済み脆弱性(KEV)カタログにはCVE-2026-125350はまだ追加されていない。

今回の更新ではCVE-2026-125350に加えて、WebGL・FileSystem・Compositing・GPU・V8・XMLコンポーネントにまたがる6件の高深刻度の脆弱性と、GPUコンポーネントにおける2件の中深刻度の脆弱性(未初期化リソースに関する問題)も修正された。

## 今後の見通し

2026年に入ってChromeで修正された悪用済みゼロデイは、これで8件目となった。V8エンジンやWebGPUのDawn、GPUコンポーネントであるSkiaなど、ブラウザの中核を支えるコンポーネントで繰り返し深刻な脆弱性が見つかっている状況は、攻撃者が依然としてChromeの複雑な内部実装を熱心に狙っていることを示している。ユーザーには、ブラウザを速やかに最新版へ更新することが強く推奨される。
