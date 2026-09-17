---
date: "2026-09-18T08:09:55+09:00"
title: "Apple、過去最大規模のセキュリティ更新を配信 ― Screen Sharingの認証バイパスは悪用済みとの分析も"
description: "Appleが9月14日にiOS 27やmacOS「Golden Gate 27」など全プラットフォーム向けに過去最大規模のセキュリティアップデートを配信し、悪用状況をめぐって報道が分かれている。"
tags:
  - Security
references:
  - "https://www.thezdi.com/blog/2026/9/16/the-apple-security-update-review-for-september-2026"
  - "https://www.theregister.com/security/2026/09/15/the-vulnpocalypse-rains-ibugs-down-on-apple-with-record-setting-number-of-patches/5296679"
  - "https://www.securityweek.com/apple-patches-200-vulnerabilities-with-new-ios-27-macos-golden-gate-27-releases/"
---

## 概要

Appleは9月14日、iOS 27・iPadOS 27・macOS「Golden Gate 27」・macOS Tahoe 26.7・visionOS 27・watchOS 27・tvOS 27・Safari 27など、ほぼ全プラットフォームを対象とした過去最大規模のセキュリティアップデートを配信した。修正件数は集計方法によって報道間で幅があり、SecurityWeekはiOS 27で約126件（うちカーネル関連20件）、macOS Golden Gate 27で210件（iOS 27と約100件が共通）、macOS Tahoe 26.7で153件（うちカーネル関連26件）と報じる一方、The RegisterはAppleの全製品を横断して260件超、Trend MicroのZero Day Initiative（ZDI）は273件のユニークなCVEと分析しており、いずれにせよAppleの歴史上最大級のパッチサイクルであることは共通している。修正はAppleKeyStore、Authentication Services、Foundation、Safe Browsing、Sandbox、Security、TCC、WebKitなど90以上のコンポーネントに及ぶ。

## 悪用状況をめぐる報道の食い違い

配信当初、The RegisterやSecurityWeekは「修正された脆弱性のいずれについても、悪用が確認されているとの記載はない」と報じ、ユーザーには念のための早急な更新を呼びかけるにとどまっていた。しかしZDIによる分析では、Screen Sharing Serverの認証バイパスの脆弱性（CVE-2026-65400、CVSS 9.8）についてCISAが実際の悪用を確認済みであるとしており、この脆弱性は有効な認証情報もユーザー操作も伴わずにネットワーク越しにScreen Sharingへ認証を通してしまうという深刻なものだ。対象はmacOS 27およびTahoe 26.7で、報道機関ごとに悪用状況の評価が分かれている点は注意が必要である。

## 注目すべき脆弱性

ZDIの分析によれば、今回のCVEのうちNVDで採点済みのものは severity 別に緊急2件、重要46件、警告84件、軽微2件で、残る139件は採点待ちとなっている。CVE-2026-65400のほかにも、Bluetoothスタックの脆弱性CVE-2026-65414（CVSS 9.8）は権限やユーザー操作を必要としないリモートコード実行を許し、8種類のOSプラットフォームに影響するという点で今回のリリース中で最も影響範囲の広い緊急脆弱性とされる。また画像処理フレームワークImageIOのCVE-2026-65346は、悪意ある画像を処理するだけで任意コード実行につながる「最も危険なリモートコンテンツ系バグ」とされ、Messagesの自動レンダリング機能により実際の攻撃に悪用されやすい構造になっている。SecurityWeekはさらに、CoreMediaのメモリ破損の脆弱性CVE-2026-64752について、Appleが該当コードを修正するのではなく完全に削除するという対応を取った点を特筆している。

## 背景と展望

The Registerは、今回のような大量のCVE公表を「vulnpocalypse」と呼び、AIによる脆弱性発見が急速に高度化している潮流の一環と位置づけている。今回修正されたCVEのうちAIが直接発見したと明記されているのは10件にとどまるが、その一例としてセキュリティ企業CalifがClaudeおよびAnthropicと協力して複数の脆弱性（少なくとも8件）を特定したことが挙げられている。企業のセキュリティ担当者からは、カーネルレベルの修正が多いことを踏まえ、即日リリースへの対応によって数週間ではなく数時間でデバイス群を最新化できる体制の重要性を指摘する声も上がっている。悪用状況の評価が報道によって割れている以上、緊急・重要度の高い脆弱性が多数含まれる今回のアップデートについては、ユーザー・組織ともに悪用の有無を待たず速やかな適用が求められる。
