---
date: "2026-03-27"
title: "VMware Aria Operationsの深刻なコマンドインジェクション脆弱性、CISAが悪用確認でKEVカタログに追加"
description: "CISAがVMware Aria Operationsのコマンドインジェクション脆弱性（CVE-2026-22719、CVSS 8.1）を既知の悪用された脆弱性カタログに追加し、連邦機関に修正を義務付けた。"
tags:
  - Security
  - Cloud
references:
  - "https://thehackernews.com/2026/03/cisa-adds-actively-exploited-vmware.html"
---

## 概要

米国サイバーセキュリティ・インフラストラクチャセキュリティ庁（CISA）は2026年3月3日、BroadcomのVMware Aria Operationsに存在するコマンドインジェクション脆弱性（CVE-2026-22719）を、既知の悪用された脆弱性（KEV）カタログに追加した。この脆弱性はCVSSスコア8.1と高い深刻度に分類されており、未認証の攻撃者がサポート支援による製品マイグレーション処理中に任意のコマンドを実行できるというものだ。野外での積極的な悪用が確認されており、連邦文民行政機関（FCEB）には2026年3月24日までにパッチを適用することが義務付けられた。

## 影響を受ける製品と修正バージョン

影響を受ける製品は、VMware Aria Operations 8.x系、VMware Cloud Foundation 9.x系、およびVMware vSphere Foundation 9.x系の3製品である。それぞれ、Aria Operations 8.18.6、Cloud Foundation 9.0.2.0、vSphere Foundation 9.0.2.0で修正されている。Broadcomは2026年2月下旬にアドバイザリをリリースしており、同時にストアド型クロスサイトスクリプティング脆弱性（CVE-2026-22720）と管理者権限への特権昇格脆弱性（CVE-2026-22721）も修正している。

## 緩和策と今後の対応

Broadcomは悪用報告について「独自に確認することはできない」としつつも、野外での悪用の可能性を認識していると述べている。即座にパッチを適用できない環境向けには、各Aria Operations仮想アプライアンスノード上でroot権限で実行する回避策シェルスクリプト（aria-ops-rce-workaround.sh）が提供されている。未認証でリモートからコード実行が可能という脆弱性の性質上、該当製品を使用する組織は早急な対応が求められる。
