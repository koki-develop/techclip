---
date: "2026-10-14T08:10:14+09:00"
title: "Microsoft、10月のPatch Tuesdayで1,400件超の脆弱性を修正、悪用済みゼロデイやOutlook経由RCEに対応急務"
description: "Microsoftが2026年10月のPatch Tuesdayで過去最多規模となる1,400件超の脆弱性を修正し、悪用が確認されたWindows Shellのゼロデイや操作不要のOutlook RCEへの迅速な対応を呼びかけている。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-october-2026-patch-tuesday-fixes-1-411-flaws-3-zero-days/"
  - "https://www.rapid7.com/blog/post/em-patch-tuesday-october-2026/"
  - "https://blog.talosintelligence.com/microsoft-patch-tuesday-for-october-2026/"
---

## 概要

Microsoftは10月13日、月例セキュリティ更新「Patch Tuesday」を公開した。修正件数は各社の集計で1,411〜1,415件と幅があるものの、いずれも過去最多規模であることは一致しており、年間を通じて脆弱性の公開数が増加し続ける傾向を裏付けるものとなった。重大度「Critical」は70〜85件とされ、そのうち過半をリモートコード実行(RCE)が占める。ゼロデイ脆弱性は3件公開され、このうちWindows Shellのセキュリティ機能バイパスであるCVE-2026-96951(CVSS 8.8)は実際の悪用が確認されており、最優先での対応が求められている。

## 悪用されたゼロデイとOutlookの重大なRCE群

CVE-2026-96951は、ファイルに付与される「Mark of the Web(MOTW)」保護機能をコマンド注入によって回避するもので、悪意あるファイルを開かせる、あるいは攻撃者が用意したサイトへ誘導するといった利用者の操作を起点に悪用される。Outlook.comのサービスにも影響が及ぶとされる。公開済みだが悪用は未確認のゼロデイとしては、Google Project ZeroのJames Forshawが発見した.NET Frameworkのセキュリティ機能バイパス(CVE-2026-108398、CVSS 8.8、Windows Defender Application Control/App Controlの制限回避につながる)、およびMessagePack-CSharpのメモリ割り当て制御不備によるサービス拒否(CVE-2026-92707)が挙げられる。

さらに深刻度の高さで注目されるのが、Outlookのプレビューウィンドウを経由する5件のRCE(CVE-2026-70242、97749、97016、88156、70291、いずれもCVSS 9.8)だ。メールを開く操作すら不要で、プレビュー表示やスクロールのみでバッファオーバーフローや二重解放(double-free)の脆弱性が悪用され得る。Rapid7は、Outlookを狙った過去の重大事例であるCVE-2023-23397に類似する危険性があると指摘し、優先的なパッチ適用を呼びかけている。Talos Intelligenceも同様にOutlook関連の複数のRCEをCVSS 9.8の最高水準と評価しており、WordやPowerPointにも深刻なRCE(CVSS 7.5〜9.8)が存在するとしている。加えて、Message Queuingのuse-after-free(CVE-2026-100202、CVSS 9.8)、Partner Centerの証明書検証バイパス(CVE-2026-96207、CVSS 10.0)、Dataverseの非信頼データの逆シリアル化(CVE-2026-88131、CVSS 9.8)など、クラウド・Azure関連でも最高水準の脆弱性が複数修正された。

## 新機能「リスクコホート」とサポート終了の節目

今回のPatch TuesdayでMicrosoftは、関連性の高い脆弱性をグルーピングして優先順位付けを支援する新機能「リスクコホート(Risk Cohorts)」を導入した。ファイルシステム・ストレージ関連(136件)、Officeドキュメント・メールクライアント(135件)、グラフィックス・メディア処理(131件)、Windowsコア・カーネルの権限境界(109件)、インストール・展開サービス(103件)といった単位でまとめられており、件数が膨大化する中で防御側が対応の優先度を判断しやすくする狙いがある。BleepingComputerは、Microsoftが脆弱性の検出・修正にAIプラットフォームの活用を続けていることも併せて紹介している。

今回は複数の製品・OSにとってサポート終了の節目にも重なる。Windows 11 version 24H2(Home/Pro)およびWindows 10 Enterprise LTSB 2016は本回が最後のセキュリティ更新となり、Windows Server 2012/2012 R2の拡張セキュリティ更新(ESU)は10月14日に、Exchange Server 2016/2019は10月15日にサポートが終了するが、ESU(拡張セキュリティ更新)プログラムの提供はない(「ESUなしクラブ」入り)。Office 2021(LTSC)もESUの提供なしに終了を迎える。Rapid7は、Microsoft Edgeの更新情報に具体的なCVEが伴わず「CVEは判明次第追加する」との注記のみで公開されている点も挙げ、防御側がパッチの緊急度を評価しにくい「可視性のギャップ」が生じていると懸念を示した。サポート終了を控える環境では、セキュリティ更新の継続性が断たれる前に移行計画を進める必要がある。
