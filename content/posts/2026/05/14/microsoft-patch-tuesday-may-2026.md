---
date: "2026-05-14T02:46:39+09:00"
title: "マイクロソフト2026年5月パッチチューズデー：120件の脆弱性を修正、AIがゼロデイなしで16件を発見"
description: "マイクロソフトは2026年5月のパッチチューズデーで120件の脆弱性を修正し、CVSS 9.8のNetlogonおよびDNSクライアントの重大なRCEを含む17件のCritical脆弱性に対応した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-may-2026-patch-tuesday-fixes-120-flaws-no-zero-days/"
  - "https://cybersecuritynews.com/microsoft-patch-tuesday-may-2026/"
  - "https://www.infosecurity-magazine.com/news/microsoft-17-critical-flaws-may/"
---

## 概要

マイクロソフトは2026年5月12日、月例セキュリティアップデート（パッチチューズデー）を公開し、Windows・Office・Azure・開発者ツールにわたる120件の脆弱性を修正した。今月はゼロデイ脆弱性の積極的な悪用は報告されておらず、先月と比べて比較的穏やかなリリースとなった。修正対象の脆弱性は深刻度別に、Critical 17件・Elevation of Privilege 61件・Remote Code Execution 31件・Information Disclosure 14件・Spoofing 13件・Denial of Service 8件・Security Feature Bypass 6件に分類される。

## 重大な脆弱性の詳細

今月特に注目すべきCritical脆弱性は以下のとおりである。

**CVE-2026-41089（Windows Netlogon、CVSS 9.8）** はスタックベースのバッファオーバーフローに起因するRCEで、攻撃に特権やユーザー操作が不要であり、攻撃複雑度も低い。セキュリティ研究者のAdam Barnett（Rapid7）は「信頼性の高いエクスプロイトの作成はさほど難しくないかもしれない」と警告しており、早急なパッチ適用が求められる。

**CVE-2026-41096（Windows DNSクライアント、CVSS 9.8）** は悪意あるDNS応答を介したRCEで、Action1のJack Bicerは「DNSはエンタープライズ環境全体で使用されるコアネットワークサービスであるため、悪用された場合、多数のシステムに迅速に影響が及ぶ可能性がある」と指摘している。

**CVE-2026-42898（Microsoft Dynamics 365 オンプレミス）** は低権限の認証済み攻撃者が悪意あるコードを実行できるCritical RCEである。そのほか、SharePoint Server（CVE-2026-40365）、Windows Word（CVE-2026-40361ほか複数）、Windows GDIコンポーネント（CVE-2026-35421）にもCritical RCEが含まれる。

## 影響範囲と優先対応

オフィス製品への攻撃ベクターとして、悪意あるファイル添付を介したWord・Excel・Officeの複数のRCEが修正されており、添付ファイルを頻繁に受け取る環境では特に迅速な対応が推奨される。クラウド・開発環境では、Visual Studio Codeに5件（CVE-2026-41613〜CVE-2026-41610、CVE-2026-41109）、Microsoft 365 Copilot、Azure Logic Apps、Azure Monitor Agentにも脆弱性が確認されている。仮想化環境ではWindows Hyper-V特権昇格（CVE-2026-40402）への対応も必要だ。

セキュリティチームはインターネットに面したサービスを優先し、Dynamics 365・SharePoint・Office RCE・DNS/Netlogonコンポーネント・グラフィックスドライバーの順で対応することが推奨されている。累積アップデートはWindows 11向けにKB5089549・KB5087420、Windows 10向けにKB5087544が提供されている。

## AIによる脆弱性発見という新潮流

今月のリリースで特筆すべきは、マイクロソフトが「MDASH」というコードネームのAI駆動セキュリティシステムを活用し、今回修正された脆弱性のうち16件を同システムが自律的に発見したことだ。MDASHは「複数モデルにまたがる100以上の専門エージェント」を採用しており、最先端モデルとコスト効率の高い蒸留モデルを組み合わせた包括的なスキャニングを行う。従来の人手による脆弱性調査にAIエージェントが大きな役割を担い始めたこの動向は、ソフトウェアセキュリティの研究プロセスにおける重要な転換点を示している。
