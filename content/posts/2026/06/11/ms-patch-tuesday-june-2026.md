---
date: "2026-06-11T03:07:11+09:00"
title: "Microsoft 2026年6月Patch Tuesday：200件の脆弱性と6件のゼロデイ修正、直後に新たなDefenderゼロデイ「RoguePlanet」も発覚"
description: "Microsoftが2026年6月のPatch Tuesdayで過去最多規模となる200件の脆弱性と6件のゼロデイを修正したが、公開直後に研究者がMicrosoft Defenderの未修正ゼロデイ「RoguePlanet」を公開した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-june-2026-patch-tuesday-fixes-6-zero-days-200-flaws/"
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-patches-yellowkey-greenplasma-miniplasma-zero-days/"
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-defender-rogueplanet-zero-day-grants-system-privileges/"
---

## 概要

Microsoftは2026年6月のPatch Tuesdayにおいて、過去最多規模となる200件のセキュリティ脆弱性を修正した。このうち33件がCritical評価であり、28件がリモートコード実行（RCE）に関するものだった。脆弱性の種類別では、特権昇格（EoP）が65件、RCEが55件、情報漏洩が30件、スプーフィングが27件、セキュリティ機能バイパスが19件、DoSが7件という内訳となっている。今回のアップデートには6件のゼロデイ修正が含まれており、そのうち5件は公開済み、1件は実際に悪用が確認されていた。

## 修正された6件のゼロデイの詳細

今回修正されたゼロデイの中でも特に注目を集めているのが、研究者「Nightmare Eclipse」によって2026年5月にパッチより約1か月前に公開された3件の脆弱性だ。同研究者はMicrosoftの脆弱性開示プロセスへの抗議としてPoC（概念実証コード）を公開していた。

- **YellowKey（CVE-2026-45585）**：Windows回復環境（WinRE）のバックドアとして機能するBitLockerバイパス脆弱性。物理アクセスを持つ攻撃者がTPM単体で保護されたシステムの暗号化を迂回可能。Windows 11およびWindows Server 2022/2025が対象。
- **GreenPlasma（CVE-2026-45586）**：Collaborative Translation Framework（CTFMON）に存在する特権昇格脆弱性。ローカル攻撃者が完全にパッチ済みのWindowsシステムでもSYSTEM権限のシェルを取得できる。
- **MiniPlasma（CVE-2020-17103）**：Cloud Files Mini Filter Driverの特権昇格脆弱性。Google Project Zeroが元々報告したもので、同様にSYSTEM権限の取得を許す。
- **HTTP/2 Bomb（CVE-2026-49160）**：HTTP.sysにおけるDoS脆弱性。HTTP/2ヘッダー圧縮を悪用してメモリ枯渇とサーバーダウンを引き起こす可能性がある。
- **CVE-2026-50507（bitskrieg）**：BitLockerのバイパスをもたらす2つ目の脆弱性。「必要なファイルにアクセスできませんでした」エラーを発生させ、WinREによる修復が必要になる場合がある。
- **CVE-2026-42897**：Exchange Server（Outlook Web Access）のスプーフィング脆弱性。細工されたメールを通じて任意のJavaScriptを実行可能で、今回唯一実際に悪用が確認されていた脆弱性。

## 修正直後に発覚した新ゼロデイ「RoguePlanet」

Patch Tuesdayのリリース数時間後、同じ研究者Nightmare Eclipseがさらに新たなゼロデイ「RoguePlanet」を公開し、セキュリティコミュニティに衝撃を与えた。この脆弱性はMicrosoft Defenderのレースコンディションを悪用するローカル特権昇格（LPE）であり、KB5094126を含む完全にパッチ済みのWindows 10/11環境（正式ビルドおよびCanaryビルドの両方）でSYSTEM権限のコマンドプロンプトを起動できることが確認されている。CVE番号は現時点では割り当てられていない。

研究者によれば、「エクスプロイトは成功するかどうかが不確定だが、一部のマシンでは100%の成功率を達成した」という。なお、元々はSMB共有上の仮想ハードディスク（.vhd/.vhdx）ファイルを対象としたRCEとして開発されたが、Microsoftの防御強化によりLPEへとダウングレードされた形だ。ThreatLockerがエクスプロイトの動作を独自に確認しており、PoCコードは研究者のセルフホスト型リポジトリで公開されている。Microsoftはまだパッチも公式声明も出していない。

## 対応と今後の見通し

今回のPatch Tuesdayは規模の大きさだけでなく、Nightmare Eclipseによる連続的なゼロデイ公開という文脈でも注目されている。同研究者はMicrosoftの脆弱性開示慣行への不満から、修正リリース前後に相次いでPoCを公開しており、今後も追加の公開が行われる可能性がある。RoguePlanetに対する暫定的な緩和策としては、アプリケーションの許可リスト（allowlisting）の導入が有効とされている。企業および個人ユーザーはできる限り早急に今月の更新プログラムを適用するとともに、RoguePlanetのパッチが提供されるまでエンドポイント保護の強化を検討することが推奨される。
