---
date: "2026-08-14T02:18:07+09:00"
title: "IntelとAMD、月例パッチで合計80件超の脆弱性を修正 特権昇格や秘密鍵漏洩のリスクに対応"
description: "IntelとAMDが2026年8月のPatch Tuesdayで合計80件を超える脆弱性を修正し、特権昇格やサービス拒否、秘密鍵漏洩、任意コード実行につながる欠陥に対処した。"
tags:
  - Security
references:
  - "https://www.securityweek.com/chipmaker-patch-tuesday-intel-amd-fix-over-80-vulnerabilities-combined/"
---

## 概要

Intelは8月12日、42件のセキュリティアドバイザリを新たに公開し、合計72件の脆弱性を修正した。AMDも同日、5件のセキュリティ通知を発行し、12件の脆弱性に対処している。両社を合わせると、今回のチップメーカー版Patch Tuesdayで修正された脆弱性は80件を超える規模となった。

## Intelの修正内容

Intelが公表した脆弱性の多くは高（High）または中（Medium）深刻度に分類される。高深刻度の欠陥は複数の製品カテゴリにまたがっており、PROSet/Wireless WiFiソフトウェアでは特権昇格・サービス拒否・ローカルコード実行につながる問題が見つかった。このほか、Xeonプロセッサでの特権昇格、Data Center Attestation Primitivesでの情報漏洩、Xeon向けAlias Checking Trusted Moduleでの特権昇格、TDXでの特権昇格、Active Management Technologyでのサービス拒否、CSMEおよびSPSでの特権昇格など、幅広い製品群で深刻な脆弱性が修正されている。

中・低深刻度の脆弱性は、PyTorch拡張機能やLLM-on-Ray、Gaudiランタイムといった AI/ML 関連ツール群やインフラ製品にも及んだ。また、Slim Bootloaderでは低深刻度の脆弱性が1件修正されている。

## AMDの修正内容

AMDが発行した5件のセキュリティ通知では、秘密鍵漏洩、特権昇格、任意コード実行につながりうる脆弱性が対処された。開発環境のVitisでは高深刻度の脆弱性が5件見つかったほか、Ryzen Master Utility、SEV-SNP、Power Design Managerでもコード実行につながる脆弱性が修正されている。AMDは以前、SEV実装に影響するサイドチャネル攻撃「PowerHooK」を公表しており、今回の修正はそれに続くセキュリティ対応の一環となる。

## 今後の対応

企業やエンドユーザーは、影響を受ける製品のファームウェアやドライバーを速やかに最新版へ更新することが推奨される。特にサーバー用途で広く使われるXeonプロセッサやSEV-SNP関連の脆弱性は、データセンター環境における機密性や可用性に直結するため、優先的なパッチ適用が望まれる。
