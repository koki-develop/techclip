---
date: "2026-06-14T02:35:04+09:00"
title: "ShinyHuntersがOracle PeopleSoftゼロデイ（CVE-2026-35273）を悪用、大学など100超の組織からデータ窃取"
description: "CVSSスコア9.8の未認証リモートコード実行ゼロデイ脆弱性CVE-2026-35273を悪用したShinyHuntersが、高等教育機関を中心とした100以上の組織のPeopleSoftシステムに侵入しデータを盗み出した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/shinyhunters-exploits-oracle-peoplesoft.html"
  - "https://www.helpnetsecurity.com/2026/06/11/oracle-peoplesoft-under-attack-cve-2026-35273/"
  - "https://www.bleepingcomputer.com/news/security/oracle-mitigates-peoplesoft-zero-day-exploited-in-data-theft-attacks/"
---

## 概要

ハッカーグループShinyHuntersが、Oracle PeopleSoft Enterprise PeopleToolsに存在するゼロデイ脆弱性CVE-2026-35273を悪用し、大学を中心とした世界100以上の組織に侵入してデータを窃取した。Googleのセキュリティ部門Mandiantはこの攻撃キャンペーンを「UNC6240」として追跡しており、活動期間は2026年5月27日から6月9日にかけてと特定している。Oracleは6月10日に帯域外のセキュリティアドバイザリを公開して緩和策を提供したが、これは攻撃期間が終了した後であり、ゼロデイとして放置されていた期間に対する批判を受けている。

## 脆弱性の技術的詳細

CVE-2026-35273はCVSSスコア9.8（Critical）の深刻な脆弱性で、PeopleSoft PeopleToolsのUpdates Environment Management（PSEMHUB）コンポーネントに存在するリモートコード実行（RCE）の欠陥だ。認証不要かつユーザー操作も必要とせず、HTTP経由のネットワークアクセスがあれば攻撃者が任意のコードを実行できる。影響を受けるバージョンはPeopleTools 8.61と8.62で、サポートが終了した旧バージョンも同様に影響を受ける可能性がある。

ShinyHuntersは本脆弱性を含む「既存の既知脆弱性と今回のゼロデイを組み合わせたガジェットチェーン」で初期アクセスを獲得したと自ら認めている。攻撃者はポート8888でPythonの`SimpleHTTP`を実行する公開ステージングサーバーを介して侵入し、MicrosoftのAzureバイナリに偽装したカスタムMeshCentralリモート管理エージェントを展開した。その後、ハードコードされた認証情報を利用したSSHによる横移動を行い、侵害されたディレクトリ内に「README-IF-YOU-SEE-THIS-YOUVE-BEEN-HACKED.TXT」というマーカーファイルを残した。

## 被害状況と影響を受けた組織

Mandiantは100以上の組織に対して脆弱性を通知したと報告している。標的となった組織の68%が高等教育機関であり、その大半が米国内の大学だ。攻撃者はおよそ300インスタンスへの侵害を確認した。被害を公表したノッティンガム大学（University of Nottingham）では、約45万5,000件のメールアドレスが漏洩し、そこには氏名・住所・電話番号・パスポート番号・障害情報といった機密性の高い個人情報が含まれていた。

ShinyHuntersはこれまでSaaSプラットフォームを主な標的としていたが、今回の攻撃はエンタープライズERPシステムへのターゲット拡大を示しており、ソーシャルエンジニアリング中心の戦術から技術的な脆弱性悪用へと能力が進化していることが示された。

## Oracleの対応と推奨される緩和策

Oracleは緊急のセキュリティアドバイザリとして、PSEMHUBサービスの無効化、またはネットワーク境界での`/PSEMHUB/*`エンドポイントへの外部アクセスのブロックを推奨している。Webアプリケーションファイアウォール（WAF）のルールのみでは不十分とされており、組織はより踏み込んだ対処が求められる。

侵害の痕跡（IoC）として、予期しない`.jsp`ウェブシェルファイル、`logs`や`persistantstorage`といった不審なディレクトリ、永続化目的で改ざんされた可能性のある最近変更されたXMLファイルが挙げられる。PeopleSoftを利用している組織はただちにパッチ適用と上記IoC調査を実施することが強く推奨される。