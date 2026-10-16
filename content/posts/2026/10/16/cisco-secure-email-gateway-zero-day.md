---
date: "2026-10-16T18:13:52+09:00"
title: "Cisco、Secure Email Gatewayの実悪用ゼロデイCVE-2026-76519(CVSS 9.8)に緊急パッチ"
description: "CiscoはSecure Email GatewayのAMP機能に存在するroot権限の任意コード実行を許すゼロデイ脆弱性CVE-2026-76519の悪用を確認し、パッチ適用とIoC確認を呼びかけた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/cisco-patches-actively-exploited-secure-email-gateway-zero-day/"
  - "https://thehackernews.com/2026/10/cisco-warns-of-active-attacks.html"
  - "https://www.securityweek.com/cisco-warns-of-exploited-secure-email-gateway-vulnerability/"
---

## 概要

Ciscoは、Secure Email Gateway(SEG)のAdvanced Malware Protection(AMP)機能に存在するゼロデイ脆弱性CVE-2026-76519(CVSS 9.8)が実際の攻撃で悪用されていることを確認し、緊急の対応を呼びかけた。この脆弱性は添付ファイルの処理における相対パストラバーサルの欠陥に起因し、認証を一切必要としない攻撃者が悪意ある添付ファイルをメールで送信するだけで、対象アプライアンスのOS上にroot権限で任意のファイルを書き込み、コマンドを実行できてしまう。CiscoはProduct Security Incident Response Team(PSIRT)経由でこの悪用を把握し、侵害痕跡(IoC)を公開するとともに早急なパッチ適用を強く推奨している。

## 脆弱性の技術的詳細と影響範囲

CVE-2026-76519は、File Reputationサービスが有効化され、AMP機能に割り当てられている環境で、Content Scanner Toolsのバージョンが25.3.0.5525より前である場合に影響を受ける。欠陥の本質は添付ファイルの取り扱いの不備で、ログイン情報を持たない送信者でもアプライアンスのオペレーティングシステムにファイルを書き込めてしまう点にある。Ciscoは2026年9月14日付けでAsyncOS 15.5.5-014および16.5.0-780、Content Scanner Tools 25.3.0.5525以降として修正版を配信していたが、報道によれば本脆弱性は当初CVE-2026-76440としてグループ化されていたとされ、その後CVE-2026-76519として独立した識別子が付与された経緯がある。

## 実悪用の確認と過去の脆弱性との関係

Ciscoは2026年10月に本脆弱性への実際の攻撃を確認したと発表している。これは、同社のSEGにおいて2025年12月以降に悪用が確認されたroot権限の脆弱性としては、CVE-2025-20393、CVE-2026-76461に続く3件目であり、SEGが短期間に相次いで攻撃者の標的となっている状況がうかがえる。この流れを受けて、米CISAは本脆弱性を既知の悪用済み脆弱性(KEV)カタログに追加し、連邦機関に対して10月17日までのパッチ適用を義務付けた。

## 推奨される対応策

Ciscoは管理者に対し、`contentscannerstatus`コマンドでContent Scanner Toolsのバージョンを確認し、Mail PoliciesでFile Reputationの有効化状況を点検した上で、直ちにパッチ済みバージョンへアップグレードするよう呼びかけている。侵害の兆候としては、システムログ内の"System Security"関連のエントリや、アプライアンス外部のネットワーク・ファイアウォールログにおける不審な通信を確認することが推奨される。仮想アプライアンスを利用している場合は、パッチ済みの新規VMを展開して設定を再構築し、証明情報を更新することが望ましい。攻撃者が侵入の証拠を消去する可能性があるため、調査と復旧の際には証拠保全にも注意を払う必要がある。
