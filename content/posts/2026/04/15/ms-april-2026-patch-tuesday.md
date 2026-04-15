---
date: "2026-04-15T18:29:59+09:00"
title: "Microsoft 2026年4月Patch Tuesday、167件修正——ゼロデイ2件（SharePoint・Defender）を含む過去2番目の規模"
description: "Microsoftが2026年4月のPatch Tuesdayで167件の脆弱性を修正。悪用が確認されたSharePointなりすまし（CVE-2026-32201）と公開済みのDefender権限昇格（CVE-2026-33825）の2件のゼロデイを含む、過去2番目に大規模なパッチリリースとなった。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-april-2026-patch-tuesday-fixes-167-flaws-2-zero-days/"
  - "https://krebsonsecurity.com/2026/04/patch-tuesday-april-2026-edition/"
  - "https://www.tenable.com/blog/microsofts-april-2026-patch-tuesday-addresses-163-cves-cve-2026-32201"
---

## 概要

Microsoftは2026年4月のPatch Tuesdayで、**167件の脆弱性**（うちCritical 8件を含む）を修正した。Tenableのセキュリティ研究者Satnam Narangが同社集計の163件を基に「過去2番目に大規模なPatch Tuesday」と評したほどの大型リリースで、うち2件はゼロデイ脆弱性だった。カテゴリ別では権限昇格が93件（全体の約57%）と最多を占め、リモートコード実行が20件、情報漏洩が21件、セキュリティ機能バイパスが13件と続く。

## ゼロデイ脆弱性の詳細

今月のゼロデイはいずれも深刻度「Important」だが、対応の緊急性は高い。

**CVE-2026-32201（SharePoint Serverなりすまし、CVSS 6.5）** はSharePoint Server 2016・2019・Subscription Editionに影響し、ネットワーク経由で認証なしに悪用できるなりすまし脆弱性だ。すでに野外での悪用が確認されており、Action1のMike Walters氏は「フィッシング攻撃、不正なデータ操作、ソーシャルエンジニアリングキャンペーンを可能にする」と警告している。

**CVE-2026-33825（Microsoft Defender権限昇格、CVSS 7.8）** は"BlueHammer"と呼ばれる脆弱性で、4月3日に研究者「Chaotic Eclipse」がGitHub上にエクスプロイトコードを公開したことで広く知られた。パッチ適用後はエクスプロイトが機能しなくなったことをWill Dormann氏が確認している。修正はAntimalware Platformのバージョン4.18.26050.3011を通じて配布されている。

## 注目すべきCritical・高CVSS脆弱性

Critical評価を受けた脆弱性の中で特に注意が必要なのが、**CVE-2026-33824（Windows IKEサービスRCE、CVSS 9.8）** だ。IKEv2が有効な環境で細工されたパケットを送りつけるだけで認証なしにリモートコード実行が可能であり、Microsoftはファイアウォールでのポート500/4500（UDP）封鎖を暫定的な緩和策として推奨している。同じくCriticalの **CVE-2026-33826（Windows Active Directory RCE、CVSS 8.0）** は同一の制限付きADドメイン内の認証済み攻撃者が悪用でき、「悪用の可能性が高い」と評価されている。また、**CVE-2026-27913（BitLockerバイパス、CVSS 7.7）** はSecure Boot/UEFIの保護を回避しうるセキュリティ機能バイパスで、エンドポイント保護の観点から影響が大きい。

## 背景とセキュリティ業界の反応

Rapid7のAdam Barnett氏は脆弱性発見件数の増加をAIの能力拡大に帰する一方、特定のプロジェクトとの直接的な関連付けには慎重な姿勢を示した。今月のパッチにはMicrosoft Edge（Chromiumベース）由来のブラウザ脆弱性が約60件含まれており、ブラウザの完全な再起動が適用完了に必要な点も強調されている。Microsoftのパッチとは別に、Adobeは4月11日にAdobe Reader（CVE-2026-34621）の緊急パッチを公開しており、こちらは2025年11月頃から悪用の痕跡があるとされる。ゼロデイを含む今月のパッチはいずれも早急な適用が推奨されている。
