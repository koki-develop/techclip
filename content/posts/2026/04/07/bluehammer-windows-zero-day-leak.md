---
date: "2026-04-07T18:22:51+09:00"
title: "Windowsゼロデイ「BlueHammer」のPoCが流出——研究者がMicrosoftの対応に不満を爆発"
description: "セキュリティ研究者がMSRCへの不満からWindowsのローカル権限昇格ゼロデイ「BlueHammer」のPoCコードをGitHubに公開し、未パッチのまま悪用リスクが高まっている。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/disgruntled-researcher-leaks-bluehammer-windows-zero-day-exploit/"
  - "https://www.technadu.com/bluehammer-zero-day-exploit-leverages-windows-privilege-escalation-prompts-security-concerns/625409/"
---

## 概要

「Chaotic Eclipse」（別名「Nightmare-Eclipse」）として知られるセキュリティ研究者が2026年4月3日、Windowsのローカル権限昇格（LPE）ゼロデイ脆弱性「BlueHammer」の概念実証（PoC）コードをGitHub上で公開した。公開の動機はMicrosoftセキュリティレスポンスセンター（MSRC）の脆弱性報告への対応に対する強い不満であると研究者自身が述べている。Microsoftは現時点で公式パッチを提供していないため、未パッチのまま脆弱性が野ざらしになる危険な状況が生じている。

## 技術的な詳細

BlueHammerはTOCTOU（Time-of-Check to Time-of-Use）競合状態とパス混乱（Path Confusion）を組み合わせた手法によるLPE脆弱性だ。攻撃に成功すると、SYSTEM権限または管理者権限の取得、SAM（Security Account Manager）データベースへのアクセス、さらにはシステムの完全掌握が可能になる。ローカルアクセスを持つ攻撃者が前提条件であり、リモートからの単独悪用には適さないが、侵害済み環境での権限昇格ステップとして非常に有効な攻撃手法となる。

セキュリティアナリストのWill Dormannはエクスプロイトの動作を実際に検証した。Windows Serverプラットフォームでは完全なSYSTEMアクセスではなく非管理者から管理者への昇格にとどまるなど信頼性に課題があると指摘したが、一般的なWindowsシステムでは権限昇格に成功することを確認している。

## Microsoftの対応と緩和策

Microsoftは「協調的な脆弱性開示（Coordinated Vulnerability Disclosure）を支持する」とコメントするにとどまり、パッチリリースの具体的な時期は明らかにしていない。研究者は「Microsoftをはったりで脅したのではない、私はまたやっている（公開する）」と述べており、開示プロセスへの不信感を露わにしている。

公式パッチが提供されるまでの緩和策として、セキュリティ専門家はローカルアクセスの厳格な監視と、認証情報の適切な管理（クレデンシャルハイジーン）の徹底を推奨している。組織は最小権限の原則を再確認し、不審なローカルプロセスの実行を検知できる体制を整えることが重要となる。
