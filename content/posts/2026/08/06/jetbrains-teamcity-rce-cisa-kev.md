---
date: "2026-08-06T20:42:51+09:00"
title: "JetBrains TeamCityにCVSS 9.8の未認証RCE脆弱性、CISAが実悪用確認しKEVカタログに追加"
description: "JetBrains TeamCity On-Premisesの認証バイパス・リモートコード実行脆弱性(CVE-2026-63077)が実際の攻撃に悪用されていることをCISAが確認し、連邦機関に8月8日までの対応を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/08/cisa-flags-teamcity-cve-2026-63077-rce.html"
  - "https://www.cisa.gov/news-events/alerts/2026/08/05/cisa-adds-one-known-exploited-vulnerability-catalog"
  - "https://securityaffairs.com/196725/security/u-s-cisa-adds-a-jetbrains-teamcity-flaw-to-its-known-exploited-vulnerabilities-catalog.html"
---

## 概要

JetBrains TeamCity On-Premisesに存在する認証バイパス・リモートコード実行(RCE)脆弱性CVE-2026-63077が実際の攻撃に悪用されていることを、米サイバーセキュリティ・インフラセキュリティ庁(CISA)が確認した。CISAは同脆弱性を8月5日付でKnown Exploited Vulnerabilities(KEV)カタログに追加し、Binding Operational Directive(BOD)に基づき連邦機関に対して8月8日までという異例の短期間での対応を義務付けている。CVSSスコアは最大値に近い9.8と評価されており、CI/CDパイプラインの中枢を担うTeamCityが未認証のまま乗っ取られ得る深刻さが際立つ。

## 脆弱性の技術的詳細

CVE-2026-63077は「デシリアライゼーション・オブ・アンtrusted・データ」に分類される脆弱性で、TeamCityのエージェント・ポーリング・プロトコルを経由して悪用される。認証を一切必要とせず、HTTP(S)でTeamCityサーバーにアクセスできる攻撃者であれば、認証チェックをバイパスしてTeamCityサーバープロセスの権限で任意のOSコマンドを実行できる。悪用に成功すると、TeamCityが保持する設定データや保存済み認証情報の窃取、サーバー設定の改ざん、さらにはビルドアーティファクトやCI/CDパイプライン全体の完全性侵害にまで発展しうる。影響を受けるのはTeamCity On-Premisesの全バージョンで、JetBrainsは修正版として2025.11.7または2026.1.3へのアップグレードを推奨している。直ちにアップグレードできない環境向けには、TeamCity 2017.1以降と互換性のあるセキュリティパッチプラグインも提供されている。

## CISAの対応と推奨される対策

CISAはKEVカタログへの追加により、連邦政府機関に対してBinding Operational Directiveに基づく法的拘束力のある対応期限(2026年8月8日)を課した。これは通常のパッチ適用サイクルと比べて極めて短く、実際の攻撃キャンペーンが進行中であることを示唆している。CISAおよびセキュリティ研究者は、民間organizationに対しても速やかなアップデート適用を強く推奨するとともに、TeamCityサーバーへのネットワークアクセス制限、インターネット公開インスタンスへのVPN経由アクセスの必須化、最小権限設定の適用、そしてTeamCityサーバーをビルドエージェントとは別の専用ホストで稼働させることを緩和策として挙げている。CI/CDツールは開発パイプライン全体への信頼の起点となるため、一度侵害されるとソフトウェアサプライチェーン全体に影響が波及するリスクがあり、早急な対応が求められる。
