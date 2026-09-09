---
date: "2026-09-09T18:14:32+09:00"
title: "Adobe、CVSS10.0のMagentoゼロデイ「StyleSmuggler」に緊急パッチ、実攻撃でRustバックドアを設置"
description: "AdobeはMagento/Adobe Commerceの認証不要コード実行ゼロデイCVE-2026-75650(StyleSmuggler)に緊急パッチを公開し、9月4日から実際に悪用されRustバックドアやPHP Webシェルが設置されていたことが判明した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/adobe-patches-magento-zero-day.html"
  - "https://www.securityweek.com/adobe-patches-over-170-vulnerabilities-including-commerce-zero-day/"
  - "https://www.bleepingcomputer.com/news/security/adobe-fixes-critical-magento-zero-day-exploited-to-backdoor-servers/"
---

## 概要

Adobeは、Magento Open SourceおよびAdobe Commerceに存在する最大深刻度(CVSS 10.0)のゼロデイ脆弱性CVE-2026-75650、通称「StyleSmuggler」に対する緊急パッチ(APSB26-146、社内管理番号VULN-39341)を公開した。Adobe自身が「悪用が確認されている」と認めているこの脆弱性は、認証なしで任意のPHPコードを実行できる深刻なもので、少なくとも9月4日から攻撃者によって実際に悪用され、サーバーへのバックドア設置に利用されていた。オランダのEコマースセキュリティ企業Sansecが攻撃を検知しており、同じくオランダのDisrexによれば、9月4日午後10時20分(UTC)の最初の悪用確認からわずか約50分後にバックドアを仕込まれたMagentoサーバーも確認されている。

## 攻撃の手口

攻撃者は、決済失敗時にリマインダーメールを描画するMagentoのテンプレート機能を悪用し、認証を経ずにPHPコードを注入していた。この手法により、少なくとも二種類のペイロードが確認されている。ひとつは外部の指令サーバーに接続するRust製のLinux向けバックドア、もうひとつは任意のPHPコマンドを実行できるWebシェルをドロップするPHP製のダウンローダーである。侵入後は永続的な足がかりを確保する目的とみられ、単なるデータ窃取にとどまらない継続的な不正アクセスのリスクが指摘されている。

## 影響範囲とAdobeの対応

影響を受けるのは、Adobe Commerce 2.4.4から2.4.9(2026年8月ビルド以前)、Adobe Commerce B2B 1.3.3から1.5.3、Magento Open Source 2.4.6から2.4.9の各バージョンである。米CISAはCVE-2026-75650を既知の悪用済み脆弱性(KEV)カタログに追加し、連邦機関に対して9月11日までの対応を義務付けた。Adobeは管理者に対し、パッチ適用だけでなく暗号鍵のローテーションと全認証情報のリセットを強く推奨している。

なお今回のパッチは、Experience Manager(107件)やAcrobat Reader(32件)、ColdFusion(9件)などを含む170件超の脆弱性修正の一環として公開されたものである。ColdFusionのコード実行脆弱性CVE-2026-48273(CVSS 9.9)やCampaign Classicのコマンド注入CVE-2026-82004(CVSS 10.0)など、他にも最高レベルの深刻度を持つ脆弱性が同時に修正されており、Adobeは優先度1に分類される更新について3日以内の適用を推奨している。
