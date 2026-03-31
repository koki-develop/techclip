---
date: "2026-04-01"
title: "Microsoft 2026年3月Patch Tuesday：79件の脆弱性を修正、ゼロデイ2件はSQL ServerとDotNET"
description: "Microsoftが2026年3月のPatch Tuesdayで79件の脆弱性を修正し、SQL Serverの権限昇格と.NETのDoSに関する公開済みゼロデイ2件を含む。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-march-2026-patch-tuesday-fixes-2-zero-days-79-flaws/"
  - "https://hackread.com/microsoft-march-patch-tuesday-two-0-days-flaws/"
---

## 概要

Microsoftは2026年3月のPatch Tuesdayにおいて、79件のセキュリティ脆弱性を修正するアップデートをリリースした。深刻度別の内訳はCritical（緊急）が3件、Important（重要）が76件で、うち2件は既に公開されていたゼロデイ脆弱性だ。種別では権限昇格（EoP）が46件と最多で、リモートコード実行（RCE）が18件、情報漏洩が10件、サービス拒否（DoS）が4件、なりすましが4件、セキュリティ機能バイパスが2件と続く。

## 2件の公開済みゼロデイ

今回のリリースで最も注目されるのは、積極的な悪用こそ確認されていないものの、既に詳細が公開されていた2件のゼロデイ脆弱性だ。

**CVE-2026-21262**（SQL Server 権限昇格）は、Microsoft SQL Serverにおける不適切なアクセス制御の問題だ。認証済みの攻撃者がネットワーク越しにシステム管理者（sysadmin）レベルまで権限昇格できる。この脆弱性はErland Sommarskogが「ストアドプロシージャにおける権限のパッケージ化」に関する論文の中で元々開示したものであり、セキュリティ研究コミュニティには以前から知られていた。

**CVE-2026-26127**（.NET サービス拒否）は、.NETプラットフォームの境界外読み取り（out-of-bounds read）に起因する欠陥で、未認証の攻撃者がネットワーク越しにサービスをクラッシュさせることが可能だ。発見者は匿名の研究者とされている。

## 注目の重大（Critical）脆弱性

今月のアップデートで特に深刻度が高いのは**CVE-2026-21536**（CVSS 9.8）で、Microsoft Devices Pricing ProgramにおけるRCEの欠陥だ。CVSSスコアが最高レベルに近く、悪用されれば重大な被害につながる恐れがある。

Officeユーザーにとって注意が必要なのが**CVE-2026-26110**と**CVE-2026-26113**だ。どちらもMicrosoft Officeに存在するRCE脆弱性で、プレビューペインを開くだけで悪用されうる点が特に危険視される。また、**CVE-2026-26144**はMicrosoft ExcelとMicrosoft Copilotを組み合わせた環境で機密データが漏洩するリスクがある情報漏洩の欠陥だ。クラウド環境では**CVE-2026-23651**をはじめとするAzure Compute Galleryの複数の脆弱性も修正対象となっており、Azure利用組織は速やかな対応が求められる。

## 影響範囲と推奨対応

修正対象のソフトウェアはSQL Server、SharePoint、Officeアプリケーション、Windowsコンポーネント（NTFS、SMB）、Active Directory、Kerberos認証、各種Azureサービスと幅広い。Hackreadはパッチ適用の優先順位として、インターネット公開されたSQL ServerやNTFS・SMBなどのネットワークサービスを最優先とし、次いでActive DirectoryやKerberosなどの認証インフラ、公開向けAPIの順で対処するよう推奨している。

Patch Tuesdayの公開後は攻撃者が修正内容を解析し、新たな悪用コードを開発する動きが活発化する傾向にある。今回の2件のゼロデイは現時点で攻撃には使われていないが、技術詳細が公開されている以上、悪用が始まるまでの時間は短い可能性がある。セキュリティチームはWindowsおよび関連製品へのパッチ適用を速やかに完了させることが強く推奨される。
