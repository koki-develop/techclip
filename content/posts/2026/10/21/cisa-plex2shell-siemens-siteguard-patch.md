---
date: "2026-10-21T18:14:00+09:00"
title: "CISAが「Plex2Shell」など6件の実悪用脆弱性をKEV入り、連邦機関に緊急パッチを命令"
description: "CISAはPlex Media Server、Siemens Software Center、SiteGuardの脆弱性6件を既知悪用脆弱性カタログに追加し、連邦機関に10月23日と11月3日を期限とする緊急パッチ適用を命じた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/10/cisa-orders-federal-agencies-to-patch.html"
  - "https://www.cisa.gov/news-events/alerts/2026/10/20/cisa-adds-six-known-exploited-vulnerabilities-catalog"
  - "https://www.heise.de/en/news/Attack-warnings-issued-for-Plex-SiteGuard-and-Siemens-Software-Center-11495087.html"
---

## 概要

米CISA(サイバーセキュリティ・infrastructure security agency)は2026年10月20日、既知悪用脆弱性(KEV)カタログに新たに6件の脆弱性を追加した。対象はPlex Media Serverの脆弱性4件(連鎖させることで未認証のリモートコード実行に至ることから「Plex2Shell」と呼ばれる)、EG Secure SolutionsのSiteGuard Server Edition、SiemensのSoftware Centerの各1件。いずれも実際の攻撃での悪用が確認されており、CISAは連邦文民行政機関(FCEB)に緊急のパッチ適用を命じた。CVE-2026-106931、CVE-2026-96656、CVE-2026-96654の3件は10月23日まで、残る3件は11月3日までの対応が求められている。

## Plex2Shellの技術的詳細

4件の脆弱性はPlex Media Server 1.43.2以前に存在する。4件の脆弱性のうち3件(CVE-2026-96652、CVE-2026-96654、CVE-2026-96655)はCVSSスコア5.3〜6.9の中程度(medium)に分類されるが、研究者Zach Mainによれば、これらを連鎖させることで未認証のリモートコード実行が可能になる。最も深刻なCVE-2026-96656(CVSS 8.6)は、デフォルトで有効になっている統計機能を通じて悪用できる「ファイル名/パスの外部制御」の欠陥。CVE-2026-96654(CVSS 6.9)はエンコードされたURIスキームの不適切な処理に起因し、CVE-2026-96652とCVE-2026-96655(いずれもCVSS 5.3)はサーバーサイドリクエストフォージェリ(SSRF)の脆弱性だ。いずれも2026年8月3日公開のビルド1.43.3.10861以降で修正されている。研究者boredhackerblogによると、実際の攻撃ではXMRigなどの暗号資金マイナーや、侵害したPlexサーバーを住宅用プロキシに転用するマルウェアの展開が確認されており、すでに実害が発生している。

## Siemens Software CenterとSiteGuardの脆弱性

Siemens Software Center(v4.0.9.8より前の全バージョン)のCVE-2026-110936(CVSS 8.4)は、意図したディレクトリではなく検索パス上からDLLを読み込んでしまう「制御されない検索パス要素」、いわゆるDLLサイドローディングの欠陥。攻撃者は正規インストーラーを装った「AllMyBasic.msi」を用いる「Romulus」ClickFixキャンペーンでこの欠陥を武器化している。一方、EG Secure SolutionsのSiteGuard Server EditionにあるCVE-2026-106931(CVSS 8.5)はOSコマンドインジェクションの欠陥で、root/SYSTEM権限での任意コマンド実行を許す。両脆弱性とも実環境での悪用がすでに確認されている。

## 影響と対応

CISAはBOD 26-04に基づき、公開資産における脆弱性のリスクベースの優先的修復を連邦機関に求めている。対象製品を利用する組織はFCEB機関に限らず速やかなパッチ適用を検討すべきだ。特にPlex2Shellはホームユーザーや、メディアサーバーをインターネットに公開している組織でも悪用リスクが高く、暗号資金マイナーやプロキシ型マルウェアの踏み台として利用される実害がすでに広がっている点に注意が必要である。
