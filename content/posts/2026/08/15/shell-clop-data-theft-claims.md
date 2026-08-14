---
date: "2026-08-15T08:03:19+09:00"
title: "ランサムウェア集団Cl0p、PTC製PLMソフトの脆弱性悪用でShellなど約50社からデータ窃取と主張"
description: "ロシア系ランサムウェア集団Cl0pが、PTC WindchillおよびFlexPLMの脆弱性を悪用してShellやPhilipsなど約50社からデータを窃取したと主張し、Shellが調査を開始した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/shell-investigates-potential-incident-after-clop-data-theft-claims/"
  - "https://www.esecurityplanet.com/threats/shell-investigates-clop-data-theft-claims-tied-to-ptc-flaw/"
  - "https://nltimes.nl/2026/08/13/russian-ransomware-group-clop-claims-cyberattacks-shell-philips"
---

## 概要

ロシア系とみられるランサムウェア集団Cl0pが、石油大手Shellやオランダの electronics 企業Philips、General Electric（GE）、Fiservなど約50社からデータを窃取したと主張していることが明らかになった。Shellは声明で「潜在的なインシデントを認識しており、セキュリティチームおよび関連の専門家と協力して調査を進めている」と述べ、正式に調査を開始したことを認めた。世界70カ国以上で約8万5000人の従業員を抱え、1日あたり2000万人の顧客にサービスを提供するShellからは、およそ89GBのデータが盗まれたとされる。Philipsからも13.5GB相当のデータが流出したと主張されているが、被害内容については各社とも調査中であり、Cl0pの主張を裏付ける第三者による検証はまだ行われていない。

## 技術的な詳細

今回の攻撃は、PTC社の製品ライフサイクル管理（PLM）ソフトウェア「Windchill」および「FlexPLM」に存在する脆弱性CVE-2026-12569を悪用したものとされる。この脆弱性は不適切な入力検証に起因するもので、Cl0pはインターネットに公開された同ソフトウェアのインスタンスを侵害し、JSP形式のWebシェルを設置してPLMシステムからデータを窃取したとみられる。Cl0pはこの手法により、Shellを含む43社の新たな被害組織をリークサイトに掲載したと報じられている。窃取されたとされるデータには、エンジニアリング図面、施設テストレポートのスキャン、施設の写真、プロジェクト計画書などが含まれるという。PTC WindchillおよびFlexPLMは航空宇宙、防衛、自動車、製造業、医療機器分野を中心に世界で3万社以上、1500以上の小売ブランドが利用する基幹システムであり、影響範囲の大きさが懸念されている。

## 背景と今後の見通し

PTCは6月17日にこの脆弱性に対するセキュリティパッチを公開していたが、米CISAは6月25日にこの脆弱性が実際に悪用されていることを確認し、既知の悪用された脆弱性（KEV）カタログに追加した。ドイツの連邦情報セキュリティ庁（BSI）も深夜に緊急警告を発し、組織に対して直ちにパッチを適用するよう求めていた。こうした警告にもかかわらず、パッチ未適用のインスタンスが標的にされたとみられる。ShellとPhilipsはいずれも調査を継続しており、GEについても同様に標的にされたと報じられているが、コメントは得られていない。Cl0pによるデータ窃取の主張は現時点では検証されておらず、今後各社の調査結果によって実際の被害範囲が明らかになるかが焦点となる。
