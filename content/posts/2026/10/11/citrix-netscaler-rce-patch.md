---
date: "2026-10-11T08:12:04+09:00"
title: "Citrix NetScalerにCVSS 9.5の深刻な脆弱性、SAML構成環境でRCEのリスク"
description: "CitrixはNetScaler ADC/GatewayのSAML構成環境を狙えるメモリオーバーフロー脆弱性CVE-2026-107406(CVSS 9.5)を修正するパッチを公開し、管理者に早急な対応を求めている。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/citrix-warns-admins-to-patch-new-netscaler-rce-flaw-immediately/"
  - "https://www.theregister.com/security/2026/10/09/citrix-gives-netscaler-admins-another-critical-reason-to-patch/5302212"
  - "https://thehackernews.com/2026/10/citrix-patches-critical-netscaler-flaw.html"
---

## 概要

Citrixは10月9日、NetScaler ADCおよびNetScaler Gatewayに存在する深刻な脆弱性CVE-2026-107406を修正するパッチを公開した。CVSS 4.0スコアは9.5で、CWE-119(メモリバッファ内操作の不適切な制限)に分類されるメモリオーバーフローの欠陥であり、悪用に成功するとリモートコード実行(RCE)またはサービス拒否(DoS)を引き起こす恐れがある。対象となるのはSAMLのIDプロバイダ(IdP)またはサービスプロバイダ(SP)として構成されたNetScaler ADC/Gatewayで、設定に"add authentication samlAction"や"add authentication samlIdPProfile"といったエントリがある環境が該当する。Citrixは現時点でこの脆弱性が実際に悪用された証拠はないとしているが、影響を受ける顧客に対し、アドバイザリを確認し早急にアップグレードするよう強く呼びかけている。

## 技術的な詳細と対象バージョン

影響範囲はSAML構成の種類によって異なる。SP構成またはIdP構成のいずれかの場合は、13.1-64.23および14.1-73.37より前の全バージョンが影響を受ける。IdP構成のみの場合は13.1-64.23から13.1-64.28まで、および14.1-73.37から14.1-73.41までのバージョンが対象となる。パッチ済みバージョンはNetScaler ADC/Gateway 14.1-73.46以降、13.1-64.29以降で、FIPS/NDcPP対応版(14.1-FIPSは73.46以降、13.1-FIPSおよび13.1-NDcPPは13.1.37.283以降)にも対応するアップデートが提供されている。なお、マネージドクラウドサービスおよびAdaptive Authenticationを利用している顧客については自動的に更新が適用されるため、個別の対応は不要という。この脆弱性はJPMorgan ChaseのXORチームに所属するMichael Tucker氏、Chew Keong Tan氏、Alex Bernier氏、および独立した研究者であるMaxim Suhanov氏によって報告された。

## 繰り返されるNetScalerの脆弱性問題

今回の修正は、NetScalerで今月相次いで報告されている脆弱性の中でも最新のものだ。The Hacker Newsによれば、CVE-2026-88771、CVE-2026-88772、CVE-2026-88779の3件はすでに実環境で悪用が確認されているという。特にCVE-2026-88772は9月上旬から政府機関、金融、教育分野を標的に悪用が検知されており、10月5日に公開されたCVE-2026-88779(CVSS 8.7)も同様に注視されている。BleepingComputerの報道では、インターネットに公開されているNetScaler機器はShadowserverの集計で約21,000台(うちゲートウェイが1,500台超、ADCが約20,000台)にのぼるとされ、CISAは2021年11月以降、ランサムウェア攻撃で悪用された7件を含め27件のCitrix製品の脆弱性が実際に悪用されたと指摘している。

## 今後の見通し

今回のCVE-2026-107406自体は悪用の証拠がないものの、過去の事例ではCitrixの脆弱性開示から短期間で悪用が始まるケースが繰り返されており、SAML構成を利用する組織は優先度を上げてパッチ適用を進める必要がある。同時に既知の悪用が確認されているCVE-2026-88771、88772、88779への対応も依然として急務であり、NetScalerを運用する管理者は複数の脆弱性に同時並行で向き合う状況が続いている。
