---
date: "2026-09-17T18:14:41+09:00"
title: "CiscoのSecure Email Gatewayに実悪用済みのゼロデイ、CISAが連邦機関に9月17日までの対応を指示"
description: "CiscoはSecure Email GatewayのCVSS9.8のSQLインジェクション脆弱性CVE-2026-76461を修正、すでに実際の攻撃で悪用されており回避策はない。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/new-cisco-secure-email-zero-day-exploited-to-execute-commands-as-root/"
  - "https://www.helpnetsecurity.com/2026/09/15/cve-2026-76461-cisco-email-gateway-zero-day-exploited/"
  - "https://securityaffairs.com/199137/hacking/cisco-warns-of-ongoing-exploitation-of-critical-email-gateway-zero-day.html"
---

## 概要

Ciscoは9月15日、Secure Email Gatewayに存在するCVSS9.8のゼロデイ脆弱性CVE-2026-76461を修正するセキュリティアドバイザリとパッチを公開した。原因はメール解析ロジックにおける検証不足で、未認証の攻撃者が悪意あるSQL文を仕込んだメールを送信するだけでSQLインジェクションが成立し、最終的にroot権限での任意コマンド実行にまで発展する。物理・仮想アプライアンスを問わず、設定内容にかかわらず影響を受ける。Cisco PSIRTはすでに実際の攻撃でこの脆弱性が悪用されていることを確認しており、アドバイザリには回避策が存在しないと明記されている。

## 影響範囲と修正版

影響を受けるのはCisco AsyncOSソフトウェアのバージョン16.5、16.0、15.5以前を実行するオンプレミスのSecure Email Gateway(物理・仮想アプライアンス)、およびクラウド提供版のCisco Secure Email Cloudである。修正版としてはAsyncOS 15.5.5-014、16.0.4-302、そして推奨版である16.5.0-780が公開されており、Ciscoはクラウド上の全デバイスをすでに16.5.0-780へ更新済みだとしている。オンプレミス環境の利用者は自ら速やかなアップグレードが求められる。

## 実悪用と検知方法

米CISAは9月14日、CVE-2026-76461を既知の悪用済み脆弱性(KEV)カタログに追加し、連邦民間機関に対して9月17日までの対応と侵害有無の確認を義務付けた。攻撃者は特殊に細工したメールメッセージ内に悪意あるSQL文を仕込み、これを起点にOS上で任意コマンドを実行する手口を用いる。Ciscoはアドバイザリの中で、mail_logs内に不審なSQL文、特に「COPY … TO PROGRAM」構文を含むエントリがないか確認するよう呼びかけており、クラスタ構成の場合は構成内の全デバイスを個別に点検する必要があるとしている。

## 今後の対応

回避策が存在しない深刻な脆弱性であり、すでに実悪用が確認されていることから、影響を受けるSecure Email Gatewayを運用する組織は速やかな修正版への更新が急務となる。CISAによる期限設定は連邦機関向けだが、メールゲートウェイは組織の境界防御における重要な位置を占めるコンポーネントであるため、民間企業においても同様の優先度での対応が推奨される。
