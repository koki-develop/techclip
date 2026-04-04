---
date: "2026-04-04T10:37:37+09:00"
title: "北朝鮮系ハッカーがDrift Protocolから285億円相当を12分で奪取——偽トークンとDurable Nonce攻撃の全容"
description: "SolanaベースのDEX「Drift Protocol」が2026年4月1日、北朝鮮国家支援ハッカーによる高度な攻撃を受け、約2億8,500万ドルの暗号資産が流出した。"
tags:
  - Security
references:
  - "https://techcrunch.com/2026/04/01/de-fi-platform-drift-suspends-deposits-and-withdrawals-after-millions-in-crypto-stolen-in-hack/"
  - "https://www.bloomberg.com/news/articles/2026-04-01/solana-based-defi-project-drift-hit-by-285-million-exploit"
  - "https://www.cryptotimes.io/2026/04/03/285m-gone-in-12-minutes-how-a-fake-token-and-stolen-keys-gutted-drift-protocol/"
---

## 概要

2026年4月1日、SolanaベースのDeFiプラットフォーム「Drift Protocol」が大規模なサイバー攻撃を受け、約2億8,500万ドル（約285億円相当）の暗号資産が流出した。被害はわずか12分間・31回の引き出しトランザクションで完結しており、2026年最大かつSolana史上2番目の規模のDeFiハックとなった。ブロックチェーン分析会社のEllipticとTRM Labsは、本攻撃を北朝鮮（DPRK）国家支援ハッカーグループによる2026年18件目の関与事例として特定した。Driftは即座に全ての入出金を停止し、$DRIFTトークン価格は40%近く暴落、プラットフォームのTVL（Total Value Locked）は55%超減少して550百万ドルから250百万ドル以下に急落した。

## 攻撃の全容——数週間にわたる周到な準備

攻撃は即興ではなく、数週間にわたって綿密に準備された。3月11日、攻撃者はTornado Cashから10ETHを引き出して資金を調達。翌12日には偽トークン「CarbonVote Token（CVT）」を7億5,000万ユニット発行し、そのうち80%を自己保有した。Raydiumのプールに500ドル程度の流動性をシードし、ウォッシュトレーディングで約1ドルの価格履歴を人工的に作り上げてDriftのオラクルに正規資産と誤認させた。

3月23〜30日にかけては「Durable Nonce（持続的ノンス）」アカウントを作成し、事前署名済みトランザクションを仕込んだ。Durable Nonceとは、Solanaにおいて通常は1回限りの使い捨てであるトランザクションのノンスを再利用可能にする仕組みで、攻撃者は実行タイミングを自在にコントロールできる状態を準備した。決定的だったのは3月27日にDrift自身がSecurity Councilのマルチシグに対するタイムロック（遅延保護）をゼロに削除したことだ。この運用上の変更が、攻撃の最終フェーズを可能にした。

## 12分間の流出と資金洗浄

4月1日正午（東部時間）、攻撃者は準備した4つの持続的ノンスアカウントのうち2つをSecurity Councilのマルチシグ署名者に紐付けて一斉に実行した。31回のトランザクションで流出した主な資産は、JLPトークン4,270万枚（約1億5,900万ドル）、Wrapped Bitcoin（1,600万ドル超）、USDC・USDT・SOLなどのステーブルコインおよびネイティブトークン。USDCは計2億3,000万ドル超がCircleのCCTP（Cross-Chain Transfer Protocol）を経由してEthereumブリッジへ送られた。著名なオンチェーン調査者ZachXBTは、Circleが凍結できる6時間の猶予があったにもかかわらず対応せず、盗難USDCのブリッジを許したとして「業界にとっての悪質プレイヤー」と強く批判した。

## 業界への影響と今後のセキュリティ対策

本攻撃が示したのは、DeFiの脆弱性のパラダイムシフトだ。LedgerのCTO Charles Guillemetは「攻撃はスマートコントラクト自体ではなく、人的・運用レイヤーを標的にしている」と指摘。Trail of Bits（2022年）やClawSecure（2026年2月）による複数の監査を通過していたにもかかわらず防げなかったことから、「分散化の幻想」への批判がコミュニティで噴出した。Solana Foundationのリリー・リューは「これはSolanaネットワーク全体の問題ではなく、アプリケーション固有の障害」とフレーミングした。

再発防止策として、管理者アクションへのハードウェア署名義務化、ガバナンス変更への24〜48時間タイムロックの業界標準化、単独否決権を持つGuardianティアの設置、Squadsなど不変マルチシグソリューションの採用拡大といった対策が業界全体で議論されている。2025年のBybitハックとの類似性も指摘されており、北朝鮮系ハッカーがコードの脆弱性よりも運用セキュリティの隙を狙う戦術に移行していることが改めて浮き彫りになった。
