---
date: "2026-09-06T18:12:01+09:00"
title: "Chromeに実攻撃で悪用中のV8ゼロデイ、Googleが緊急パッチ配布——2026年6件目"
description: "GoogleはChromeのV8エンジンに存在する型混同の脆弱性CVE-2026-85046を含む12件の脆弱性を緊急修正し、実際の攻撃での悪用を確認したとして早急なアップデートを呼びかけている。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/google-releases-chrome-update-to-patch.html"
  - "https://www.bleepingcomputer.com/news/security/google-warns-of-new-chrome-zero-day-flaw-exploited-in-attacks/"
  - "https://www.helpnetsecurity.com/2026/09/04/google-chrome-zero-day-cve-2026-85046/"
---

## 概要

Googleは9月3日から4日にかけて、ChromeのStableチャンネル向けに緊急セキュリティアップデートを配布し、JavaScript/WebAssemblyエンジン「V8」に存在する型混同の脆弱性CVE-2026-85046（CVSS 8.8）を含む合計12件の脆弱性を修正した。この脆弱性はすでに実際の攻撃で悪用されていることをGoogle自身が確認しており、細工されたHTMLページを閲覧するだけでサンドボックス内での任意コード実行を許してしまう危険性がある。修正版はWindows/macOS向けがChrome 152.0.7977.82/.83、Linux向けが152.0.7977.82で、ユーザーには早急な更新が呼びかけられている。

## 脆弱性の技術的詳細

CVE-2026-85046を発見したセキュリティ研究者Salvatore Gulizia（ハンドル名「Serotav」）氏の分析によれば、この脆弱性はV8のコンパイラに起因する型混同バグで、「PACKED_ELEMENTSを含む配列がPACKED_SMI_ELEMENTSのマップを受け取ってしまう」ことでJavaScriptヒープ上の任意の読み書きが可能になるという。攻撃者は悪意あるJavaScriptを埋め込んだHTMLページを閲覧させるだけで、Chromeのレンダラープロセスのサンドボックス内でコードを実行できる。Gulizia氏はこの脆弱性を8月4日に報告し、責任ある開示に対して1,000ドルのバグバウンティを受け取っている。なお、Googleは悪用の拡大を防ぐため、通例どおり技術的な詳細の全面公開をパッチ適用が広まるまで控えている。

## 2026年6件目のゼロデイという文脈

CVE-2026-85046は、2026年に入ってから実際の攻撃で悪用が確認されたChromeゼロデイとしては6件目にあたる。これまでにもCVE-2026-2441、CVE-2026-3909、CVE-2026-3910、CVE-2026-5281、CVE-2026-11645がV8やCSSFontFeatureValuesMap、Skiaグラフィックスライブラリ、WebGPU実装などで見つかっており、Chromeのレンダリング・実行系コンポーネントが継続的に標的とされている実態が浮かび上がる。今回の脆弱性は米CISAの「既知の悪用された脆弱性」カタログにも追加され、米連邦機関には9月18日までのパッチ適用が義務付けられた。

## 対応と影響範囲

Chromeユーザーは「設定」→「Chromeについて」から手動でアップデートを確認し、直ちに適用することが推奨される。ChromiumをベースとするEdge、Brave、Opera、Vivaldiなど他のブラウザも同様の脆弱性の影響を受ける可能性があり、各ベンダーからの修正版リリースまでには数日程度を要する見込みだ。すでに実攻撃での悪用が確認されている以上、対象ブラウザの利用者は自身の更新状況を速やかに確認することが望ましい。
