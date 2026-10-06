---
date: "2026-10-07T08:12:33+09:00"
title: "Dell System UpdateにCVSS 9.6の重大パストラバーサル脆弱性、未認証でroot権限奪取の恐れ"
description: "Dell PowerEdgeサーバー向け更新ツール「Dell System Update」にCVSS 9.6の未認証パストラバーサル脆弱性が見つかり、Dellがバージョン2.3.0.0以降への緊急アップデートを呼びかけている。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/new-dell-system-update-flaw-lets-hackers-gain-root-privileges/"
  - "https://www.helpnetsecurity.com/2026/10/06/dell-system-update-vulnerability-cve-2026-86360/"
  - "https://securityaffairs.com/200458/security/dell-urges-customers-to-patch-critical-dsu-flaw-that-can-give-attackers-root-access.html"
---

## 概要

Dellは、企業のPowerEdgeサーバー向けにBIOSやファームウェア、ドライバの更新を行うコマンドラインツール「Dell System Update(DSU)」バージョン2.3.0.0未満に、重大なパストラバーサル脆弱性(CVE-2026-86360)が存在すると発表した。CVSSスコアは最大値に近い9.6で、認証を経ていない攻撃者がリモートからネットワーク経由でこの脆弱性を悪用できる点が深刻度を押し上げている。Dellのセキュリティアドバイザリ(DSA-2026-324)によれば、悪用に成功した場合、攻撃者はファイルシステムへのアクセス権を得たうえでroot権限による任意コード実行が可能となり、対象アプリケーションと基盤となるOSが完全に侵害される恐れがあるという。対象はLinuxとWindowsの両方で動作するDSUで、Dellは顧客に対しバージョン2.3.0.0以降へ直ちにアップグレードするよう強く呼びかけている。

## 技術的な詳細

CVE-2026-86360はパストラバーサル型の脆弱性で、本来アクセスが制限されているべきファイルパスの検証が不十分なために発生する。Dellは公式説明で「認証されていない攻撃者がリモートアクセスを通じてこの脆弱性を悪用し、攻撃者によるファイルシステムアクセスにつながる可能性がある」としており、最終的にはroot権限での任意コード実行に至る。この脆弱性の報告者はOri Gabrielとされている。

同時に公開されたアドバイザリでは、関連する4件の高深刻度の脆弱性も修正された。Ori Gabrielが報告したCVE-2026-63697(CVSS 7.6、証明書検証不備によるリモートコード実行)、Cipher Security LabsのNir Yehoshuaが報告したCVE-2026-71168(CVSS 7.3、パストラバーサルによるローカルからリモートへのコード実行)、そしてsaltedfishが報告したCVE-2026-86361およびCVE-2026-86362(いずれもCVSS 8.2、不適切な権限設定による権限昇格)である。これとは別に、DellのContainer Storage Module(CSM)でも最大深刻度の脆弱性2件(CVE-2026-63688、CVE-2026-63692)が指摘されている。

## 影響と対応

現時点でこれらの脆弱性が実際に悪用された事例は報告されていない。ただし、パストラバーサルの脆弱性は2007年以降「許されざるもの(unforgivable)」と位置づけられてきた。FBIとCISAも2024年5月以降、ベンダーに対して製品リリース前の段階でこの種の脆弱性を根絶するよう求めている。過去には国家支援を受けた攻撃グループ(北朝鮮のLazarusや中国系とされるUNC6201など)が別のDell製品の脆弱性を悪用した例もあり、今回のDSUの脆弱性についても早期の対応が強く推奨される。Dellは該当するPowerEdgeサーバーの管理者に対し、DSUをバージョン2.3.0.0以降へ速やかに更新するよう重ねて呼びかけており、企業の情報システム部門は自社環境でのDSU利用状況を確認し、優先度の高いパッチ適用対象として扱う必要がある。
