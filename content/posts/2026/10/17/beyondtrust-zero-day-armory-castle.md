---
date: "2026-10-17T18:12:03+09:00"
title: "中国系スパイ集団Armory Castle、BeyondTrust Remote Supportのゼロデイを8月から悪用しルート権限を窃取"
description: "中国系の疑いがある国家支援ハッカー集団Armory Castleが、BeyondTrust Remote Supportの認証バイパス脆弱性CVE-2026-102764を8月下旬から悪用し、カスタムマルウェアでリモートサポートサーバーを乗っ取っていたことが判明した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/beyondtrust-patches-zero-day-exploited-in-attacks-since-august/"
  - "https://thehackernews.com/2026/10/china-linked-hackers-exploited.html"
  - "https://cloud.google.com/blog/topics/threat-intelligence/armory-castle-exploits-beyondtrust"
---

## 概要

BeyondTrustは、Remote SupportおよびPrivileged Remote Accessに存在する認証バイパスの脆弱性(CVE-2026-102764、CVSS 9.3)に対する修正パッチを公開した。この脆弱性は、中国との関連が疑われるスパイ活動集団「Armory Castle」(旧称UNC5221、別名Warp Panda)によって、公表前の8月下旬からゼロデイ攻撃に悪用されていたことがGoogle Threat Intelligence Group(GTIG)とMandiantの分析で判明している。脆弱性は内部メッセージングコンポーネントの発信元検証不備に起因し、非特権の攻撃者がリモートで任意のファイル操作を行えるというもので、攻撃者はこれを足がかりにWebサービスアカウントからルート権限まで昇格させていた。CISAは本脆弱性を既知の悪用脆弱性(KEV)カタログに追加し、連邦政府機関に10月19日までのパッチ適用を義務付けている。

## 攻撃の手口

Armory Castleは2023年10月から活動が確認されている集団で、CitrixやIvantiのエッジアプライアンスを標的にした過去のゼロデイ攻撃との手法的な類似性から帰属が判断された。今回の攻撃では、影響を受けるバージョン24.3.1から26.2.3の自己ホスト型BeyondTrust appliance上で、独自開発のPHP製Webシェル「SAWFLY」(ファイル名mangoapi.php)を展開。SAWFLYはBase32エンコーディングと256bit RC4暗号を組み合わせた双方向の暗号化C2通信を行い、所定のパラメータが存在しない場合は404を返してスキャナーの検知を回避する仕組みを備えていた。

侵入後は`/bin/sh`を`/usr/bin/dbus-authd`としてコピーしSUID権限を付与することでルートへの権限昇格を実現し、`bt-secrets`コマンドでサイトサービスアカウントの認証情報をvaultから窃取した。さらに起動時に自動実行されるスクリプトやsudoers設定の改変によって再起動後も持続する永続化を確立し、侵害した管理者アカウントの権限をAdministratorへ昇格させて横展開を行った。ネットワーク内部へのトンネリングには、C言語で書かれたSOCKS5プロキシツール「BARECLAW」をWebSocket経由で稼働させ、HAProxy設定を改変してバックドアアクセス用の内部経路を構築していた。最後にauth.logやssl.logなど複数のログファイルを削除し、侵入の痕跡を消去するアンチフォレンジック行為も確認されている。

## 影響と対応

BeyondTrustによれば、SaaS版の顧客には10月8日に自動的にパッチが適用済みだが、自動更新を無効にしている自己ホスト型の導入環境では手動でのパッチ適用が必要となる。悪用の経路が確認されていないPrivileged Remote Accessについても、予防的措置としてパッチが提供された。BeyondTrustは今回で、CitrixやIvantiのエッジアプライアンスと同様に、国家支援ハッカーに狙われるリモートアクセス製品として繰り返し名前が挙がる結果となった。GTIGは、脆弱性の公開を受けてArmory Castleの過去のパターンに倣い、他の攻撃者による広範な便乗悪用が今後発生する可能性が高いと警告している。該当製品を利用する組織には、パッチの即時適用に加え、外部からのアクセス制限、vaultおよび管理者認証情報のローテーション、ユーザー権限変更やAPIアカウントの監査、外部SIEMへのログ転送などの対応が求められる。
