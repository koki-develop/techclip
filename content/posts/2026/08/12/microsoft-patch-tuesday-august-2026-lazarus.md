---
date: "2026-08-12T08:13:29+09:00"
title: "Microsoft 8月のPatch Tuesdayで400件超修正、Lazarusが悪用したWinSockゼロデイに対応"
description: "Microsoftが2026年8月の月例更新で400件超の脆弱性を修正し、北朝鮮系Lazarusグループが実際に悪用していたWinSock用ドライバのゼロデイ(CVE-2026-68820)を含む3件のゼロデイに対応した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-august-2026-patch-tuesday-fixes-400-flaws-3-zero-days/"
  - "https://thehackernews.com/2026/08/microsoft-patches-398-flaws-including.html"
  - "https://www.theregister.com/security/2026/08/11/421-bugs-in-microsofts-patch-tuesday-release-and-the-norks-have-already-attacked-one/5286483"
---

## 概要

Microsoftは2026年8月の月例パッチ「Patch Tuesday」を公開し、集計方法によって400件前後（Zero Day Initiativeベースで398件、The Registerの独自集計では421件）に上る脆弱性を修正した。このうち3件はゼロデイ脆弱性で、なかでもWinSock用補助関数ドライバ(afd.sys)に存在するCVE-2026-68820は、パッチ公開前から北朝鮮系脅威アクターLazarusグループによって実際に悪用されていたことが明らかになっている。7月の記録的な570件規模の修正からは件数が減少したものの、AIを活用した脆弱性発見システムの導入により、Microsoftの月例更新は例年より大幅に多い件数が「新常態」になりつつあるとThe Registerは指摘している。

## ゼロデイ脆弱性の詳細

積極的に悪用が確認されているCVE-2026-68820は、カーネルのネットワーキングコンポーネントであるWindows Ancillary Function Driver for WinSock(afd.sys)に存在するuse-after-free脆弱性で、CVSSスコアは7.0。攻撃者はローカルで実行中のコードを起点に、特別に細工したアプリケーションで競合状態(race condition)を発生させることでSYSTEM権限への昇格が可能になる。Check Point Researchはこの脆弱性をLazarusグループの「Operation Dream Job」キャンペーンと関連付けており、同社の脅威インテリジェンス責任者は「このCVEの成功した実装を1件確認しているが、キャンペーン全体で広く使われていたと見ている」とコメントした。発見者はCheck PointのMoshe Marelus氏とDavid Driker氏。

このほか、公開情報として既知だったゼロデイが2件ある。管理者権限の奪取を可能にするWindows User Profile Serviceの昇格脆弱性CVE-2026-62832(通称「LegacyHive」、リンク参照の不備が原因)と、レジストリハイブの改ざんを許すWindows Container Isolation FS Filter Driverの脆弱性CVE-2026-72971だ。

## Lazarusによる悪用キャンペーンの実態

The Registerによれば、Lazarusはこの脆弱性を6月上旬という早い段階から兵器化していた。標的となったのは欧州とインドの防衛関連組織で、攻撃者はロッキード・マーティンやプライバシー技術企業Enveilになりすまし、検索エンジンで上位表示されるよう最適化した偽の採用サイトを用意していたという。攻撃の実行段階では、改変されたPDFビューア「SecurityPDF」を配布し、細工されたPDF文書から悪意あるペイロードを実行、これまで知られていなかったバックドア「Troy」を展開した。その後、afd.sysの競合状態を突いてカーネルモードのルートキット「FudModule」を仕込み、権限昇格を完了させる流れだ。

## 重大なリモートコード実行脆弱性

今回の更新では、認証不要かつユーザー操作なしで悪用できるCVSS 9.8の重大なRCE脆弱性が複数含まれる。Windows DNS Serverのスタックベースバッファオーバーフロー(CVE-2026-62878)は「ワーム化可能」と評価されており、Windows Deployment ServicesのTFTPハンドリングに存在するCVE-2026-62893は認証不要のUDPポート69経由で悪用可能。ほかにMicrosoft QUICのRCE(CVE-2026-62815)も重大度Criticalとされた。またSharePointでは、7月に修正された認証バイパス脆弱性CVE-2026-55040と、今回修正されたRCE脆弱性CVE-2026-63520が組み合わさることで、認証なしの攻撃チェーンが完成する形になっており、2ヶ月にまたがる修正の一環として注目されている。このほかWindows DNS Server、DHCP Server、SSTP、iSCSI Target Serviceなどにも重大なRCE脆弱性が見つかっており、Exchangeの権限昇格脆弱性CVE-2026-62911はPwn2Own Berlinで実演されたものだ。

## 今後の対応

Microsoftは重大度Critical相当の脆弱性を42件(ZDI集計では62件)含む今回の更新の速やかな適用を推奨している。特にCVE-2026-68820は攻撃キャンペーンで既に悪用が確認されており、また複数の重大なRCE脆弱性が認証不要で悪用可能であることから、企業のセキュリティ担当者には優先度の高いパッチ適用が求められる。AIによる脆弱性発見の効率化を背景に、今後も大規模な月例更新が続く可能性が高く、パッチ管理体制の見直しが必要になりそうだ。
