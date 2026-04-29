---
date: "2026-04-30T02:37:03+09:00"
title: "CISAがConnectWise ScreenConnectとWindows Shellの脆弱性をKEVに追加、Storm-1175による悪用継続を確認"
description: "CISAはConnectWise ScreenConnect（CVE-2024-1708）とMicrosoft Windows Shell（CVE-2026-32202）の2件の脆弱性を既知悪用脆弱性カタログに追加し、連邦機関に2026年5月12日までの修正適用を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/cisa-adds-actively-exploited.html"
  - "https://www.cisa.gov/news-events/alerts/2026/04/28/cisa-adds-two-known-exploited-vulnerabilities-catalog"
  - "https://securityaffairs.com/191442/security/u-s-cisa-adds-microsoft-windows-shell-and-connectwise-screenconnect-flaws-to-its-known-exploited-vulnerabilities-catalog.html"
---

## 概要

米国サイバーセキュリティ・インフラセキュリティ庁（CISA）は2026年4月28日、ConnectWise ScreenConnect の CVE-2024-1708 および Microsoft Windows Shell の CVE-2026-32202 を既知悪用脆弱性（KEV）カタログに追加した。両脆弱性はすでに実際の攻撃で積極的に悪用されていることが確認されており、拘束的運用指令（BOD 22-01）に基づき、連邦民間行政機関（FCEB）は2026年5月12日までの修正適用が義務付けられている。CISA は民間組織に対しても優先的な対応を強く推奨している。

## 各脆弱性の詳細

**CVE-2024-1708（ConnectWise ScreenConnect）** は、ScreenConnect バージョン 23.9.7 以前に存在するパストラバーサル脆弱性で、CVSS スコアは 8.4。ファイルパスの制限が不適切なため、攻撃者は本来アクセスできないファイルやディレクトリに到達でき、リモートコード実行や機密データへの不正アクセスにつながる恐れがある。本脆弱性は2024年2月に修正済みであるにもかかわらず、中国関連の脅威アクター「Storm-1175」によって現在も積極的に悪用されている。

**CVE-2026-32202（Microsoft Windows Shell）** は、Windows Shell の保護メカニズムの失敗を突くスプーフィング脆弱性で、CVSS スコアは 4.3。攻撃者はネットワーク越しにコンテンツを詐称できる。Akamai の分析によると、本脆弱性は、APT28（別名 Fancy Bear）が CVE-2026-21513 と組み合わせて2025年12月以降ウクライナおよび EU 諸国への攻撃でゼロデイとして悪用していた CVE-2026-21510 の不完全なパッチから生じている。CVE-2026-32202 自体を悪用している攻撃の性質については、Microsoft は公表していない。修正パッチは2026年4月のアップデートで提供された。

## 背景と影響

KEV カタログへの追加は、脆弱性が単に理論上のリスクにとどまらず、現実の攻撃に実際に利用されていることを示す重要なシグナルである。特に CVE-2024-1708 は修正から2年以上が経過しているにもかかわらず悪用が継続しており、パッチ適用の徹底が依然として組織にとっての課題であることを浮き彫りにしている。CVE-2026-32202 については、前回パッチの不完全さが新たな攻撃ベクターを生んだ点が注目される。ConnectWise ScreenConnect を利用する組織はバージョンを最新版に更新し、Windows 環境では2026年4月のセキュリティ更新プログラムの適用を速やかに行うことが求められる。
