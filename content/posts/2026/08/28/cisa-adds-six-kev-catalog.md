---
date: "2026-08-28T21:53:52+09:00"
title: "CISA、悪用が続くCitrix NetScalerや7年前のSQL Server脆弱性など6件をKEVカタログに追加"
description: "CISAがCitrix NetScalerの新規脆弱性や7年前に公開されたMicrosoft SQL Serverの脆弱性など6件を既知の悪用脆弱性(KEV)カタログに追加し、連邦機関に8月29日と9月9日を期限とした修正を義務付けた。"
tags:
  - Security
references:
  - "https://www.cisa.gov/news-events/alerts/2026/08/26/cisa-adds-six-known-exploited-vulnerabilities-catalog"
  - "https://www.infosecurity-magazine.com/news/cisa-kev-microsoft-citrix/"
  - "https://thehackernews.com/2026/08/cisa-adds-six-exploited-flaws-to-kev.html"
---

## 概要

米サイバーセキュリティ・インフラセキュリティ庁(CISA)は8月26日、実際に悪用が確認された脆弱性6件を既知の悪用脆弱性(KEV)カタログに新たに追加したと発表した。対象にはCitrix NetScaler ADC/Gatewayのメモリ関連脆弱性、7年前にパッチが公開されながら今なお攻撃が続くMicrosoft SQL Serverのリモートコード実行(RCE)脆弱性、さらにRed Hat製品やLinuxカーネル、サードパーティ製.NETライブラリの古い脆弱性が含まれる。連邦民間行政機関(FCEB)には、拘束的運用指令(BOD 26-04)に基づき8月29日または9月9日までの修正が義務付けられており、CISAは民間組織に対しても同様の対応を強く推奨している。

## 現在進行形で悪用されるCitrix NetScalerの脆弱性

もっとも緊急性が高いのがCVE-2026-8452で、Citrix NetScaler ADCおよびNetScaler Gatewayに存在するメモリバッファ境界外操作の脆弱性(CVSS 8.8)だ。ゲートウェイ機能(VPN仮想サーバ、ICAプロキシ、CVPN、RDPプロキシなど)が有効な構成で影響が大きく、サービス拒否や予測不能な動作を引き起こす恐れがある。実際の攻撃では、12個のIPアドレスから36件の悪用試行が検出されており、侵害後に攻撃者が「x.php」「z.php」といったウェブシェルを設置している事例も確認されている。Citrixはすでに14.1-72.61以降、13.1-63.18以降など複数バージョンで修正パッチを提供済みで、CISAは連邦機関に8月29日までの対応を求めている。

もう一つの緊急案件がCVE-2019-1068で、Microsoft SQL Serverのリモートコード実行脆弱性(CVSS 8.8)だ。特別に細工したクエリを送信することで、SQL Server Database Engineサービスアカウントの権限でコードを実行できる。パッチ自体は7年前から公開されているにもかかわらず、パッチ未適用のシステムが今も攻撃対象になっている点が改めて浮き彫りになった。こちらもCitrixの脆弱性と同じく8月29日が修正期限とされている。

## 数年〜十年以上前の古い脆弱性も対象に

残る4件は9月9日を期限とし、いずれも公開から年月が経過した脆弱性だ。LinuxカーネルのCVE-2022-0995はメモリ境界外書き込みの脆弱性(CVSS 7.8)、Red Hatの自動バグ報告ツール(ABRT)のCVE-2015-5287はシンボリックリンク攻撃による権限昇格の脆弱性(CVSS 7.8)、同じくRed Hatのlibuserに存在するCVE-2015-3246は競合状態により`/etc/passwd`ファイルの破損を招く可能性がある脆弱性(CVSS 5.1)。さらにサードパーティ製の.NETライブラリAjax.NET Professional(AjaxPro)のCVE-2021-23758は、信頼できないデータのデシリアライズによりリモートコード実行につながる脆弱性(CVSS 8.1)だ。中には10年以上前に公開されたものも含まれており、レガシーシステムがいまだに攻撃者の標的として有効であることを示している。

## 影響と対応

KEVカタログへの追加は、実環境での悪用が確認された脆弱性を対象にしており、連邦機関には期限内のパッチ適用が義務化される一方、民間企業や組織にとっても優先度の高い修正対象を知る重要な指標となる。特にCitrix NetScalerは公開されたRCEやウェブシェル設置の実例があることから優先的な対応が求められる。またSQL Serverの脆弱性のように、パッチが長期間存在していても未適用環境が攻撃を受け続けている実態は、資産管理とパッチ運用の徹底がセキュリティ対策の基本であることを改めて示している。
