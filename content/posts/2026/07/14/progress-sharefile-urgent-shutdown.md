---
date: "2026-07-14T02:40:41+09:00"
title: "Progress ShareFile、正体不明の脅威でStorage Zone Controllerの緊急停止を顧客に要請"
description: "Progress SoftwareがShareFileのStorage Zone Controllerを標的とした「信頼性の高い外部からの脅威」を認識し、顧客にサーバーの手動停止を緊急要請、一部アカウントも予防的に無効化した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/07/urgent-progress-tells-sharefile.html"
  - "https://www.bleepingcomputer.com/news/security/progress-urges-sharefile-customers-to-shut-down-servers-over-credible-threat/"
  - "https://www.helpnetsecurity.com/2026/07/13/progress-sharefile-security-threat/"
---

## 概要

Progress Softwareは2026年7月10日、ファイル共有サービス「ShareFile」のオンプレミスコンポーネントであるStorage Zone Controllerを標的とした「信頼性の高い外部からの脅威(credible external security threat)」を確認したとして、顧客に対しWindowsサーバーの手動での緊急停止を要請した。同社は予防的措置として一部のShareFileアカウントを一時的に無効化しており、Storage Zone Controllerを利用する顧客はShareFileへのアクセスができない状態が続いている。Progressは「Progress ShareFileのアカウントやデータへの不正アクセスを示す痕跡は確認していない」としているが、脅威の具体的な内容や攻撃者の正体については明らかにしていない。

## 技術的な詳細

Storage Zone Controllerは、ShareFileのクラウドプラットフォームと顧客が管理するオンプレミスストレージとの間でファイル転送を仲介する、顧客管理下のWindowsサーバーだ。ユーザーがファイルをアップロード・ダウンロードする際、ShareFileはリクエストをこのControllerへ振り分けてファイルの保存・取得を行う構造上、インターネットからアクセス可能な状態で運用されるケースが多い。Progressはパッチ適用ではなく手動でのサーバー停止を求めており、これは既知の脆弱性に対する修正プログラムがまだ存在しないか、あるいは盗まれた認証情報や侵害されたインフラといったパッチでは対処できない性質の脅威である可能性を示唆している。Help Net Securityの報道によれば、セキュリティコミュニティの一部では、CVE-2026-2699とCVE-2026-2701という2件の脆弱性を組み合わせることで、未パッチ環境において認証前のリモートコード実行(pre-auth RCE)が可能になるとの未確認の推測が広がっているという。ただしProgressはこの原因について公式には確認していない。

## 背景

今回の対応は、2023年にCitrix(当時のShareFileの運営元)がStorage Zones Controllerの未認証脆弱性CVE-2023-24489を悪用された事例を彷彿とさせる。Progressは2024年にShareFileを買収したが、その前にはClop恐喝グループが自社製品「MOVEit Transfer」のゼロデイ脆弱性を悪用し、数千の組織に影響を及ぼした大規模インシデントも経験している。エンタープライズ向けファイル共有製品が繰り返し標的とされてきた経緯があり、今回もその延長線上にあるとみられる。

## 影響と今後の見通し

Storage Zone Controllerを利用するShareFile顧客は現時点で業務に支障が出ており、Redditなどでは顧客からProgressの情報提供の少なさや復旧時期の不透明さに対する不満の声も上がっている。Progressは社内外のセキュリティ専門家と協力して脅威の評価を進めており、当初は24時間以内の続報を約束していた。アクセスは段階的に復旧されつつあるが、脅威の正体やサーバー再稼働の許可時期について、顧客への正式な説明が待たれる状況だ。
