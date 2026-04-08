---
date: "2026-04-08T10:38:28+09:00"
title: "QilinとWarlockランサムウェアがBYOVD手法で300以上のEDRツールを無効化、Cisco TalosとTrend Microが解析"
description: "QilinおよびWarlockランサムウェアグループが、脆弱なカーネルドライバーを悪用するBYOVD手法により300以上のEDRセキュリティツールを無効化していることが、Cisco TalosとTrend Microの調査で明らかになった。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/qilin-and-warlock-ransomware-use.html"
  - "https://securityboulevard.com/2026/04/qilin-and-warlock-ransomware-use-vulnerable-drivers-to-disable-300-edr-tools/"
---

## 概要

QilinおよびWarlockという2つのランサムウェアグループが、BYOVD（Bring Your Own Vulnerable Driver）と呼ばれる手法を用いて、標的環境に存在する300以上のEDR（エンドポイント検知・応答）ツールを無効化していることが判明した。Cisco TalosはQilinの攻撃手法を、Trend MicroはWarlock（「Water Manaul」とも追跡）の活動をそれぞれ調査・公開した。BYOVDはWindowsカーネルレベル（Ring-0）で動作する正規署名済みの脆弱なドライバーを悪用する手法であり、ユーザーモードで動作するセキュリティ製品では検知・阻止が困難な点が問題視されている。

現在、Qilinは最も活発なランサムウェアグループの一つとなっており、2025年に日本国内で発生した134件のランサムウェア事案のうち22件（約16.4%）に関与しているとされる。また、初期侵害から暗号化実行までの潜伏期間は平均約6日間とされており、防御側に対応の余地はあるものの、その間に検知できなければ甚大な被害が生じるリスクがある。

## Qilinの攻撃チェーン

Cisco TalosのTakahiro TakedaとHolger Unterbrinkによると、Qilinの攻撃はDLLサイドローディングを起点とする多段階の手法を採用している。まず**msimg32.dll**という悪意のあるDLLが展開され、これが第1ステージのPEローダーとして機能する。このローダーは実行環境を整え、暗号化された第2ステージのペイロードを内包しており、すべてインメモリで動作することで検知を回避する。

具体的には以下の順序で処理が進む。

1. EDR製品が利用するユーザーモードフックを無効化し、APIコールの監視を妨害する
2. Windowsのイベントトレーシング（ETW）によるログ生成を抑制する
3. EDRキラーコンポーネントがEDRの監視コールバックを登録解除し、プロセス終了を妨げられない状態を作る
4. 脆弱なドライバー**rwdrv.sys**（ThrottleStop.sys のリネーム版）と**hlpdrv.sys**をロードし、300以上のEDRドライバーに関連するプロセスを強制終了する
5. ランサムウェアの本体をインメモリで実行する

なお、**rwdrv.sys**と**hlpdrv.sys**は以前AkiraおよびMakopランサムウェアのBYOVD攻撃でも使用された実績があり、複数の脅威アクター間でツールやインフラが共有されている可能性を示唆している。

## Warlock（Water Manaul）の攻撃手法と更新されたツールキット

Trend Microが追跡するWarlockは、パッチ未適用の**Microsoft SharePointサーバー**を初期侵入経路として使用する点が特徴的だ。2026年1月にはツールキットが更新され、従来使用していたBYOVDドライバー**googleApiUtil64.sys**が**NSecKrnl.sys**（NSec製）に置き換えられた。このドライバーはカーネルレベルでセキュリティ製品を終了させるために使用される。

Warlockの攻撃で観測されたツールキットには以下が含まれる。

- **TightVNC** — 永続的なリモートコントロール
- **PsExec** — ラテラルムーブメント（横移動）
- **RDP Patcher** — 複数同時RDPセッションの有効化
- **Velociraptor** — C2通信
- **Visual Studio Code + Cloudflareトンネル** — C2通信のトンネリング
- **Yuze** — イントラネット侵入・リバースプロキシ
- **Rclone** — データ窃取

## 推奨される対策と今後の展望

Trend MicroはBYOVD攻撃への対策として、「基本的なエンドポイント保護から、厳格なドライバー管理とカーネルレベル活動のリアルタイム監視への移行が不可欠」と強調している。具体的な推奨策としては、信頼できる発行元のドライバーのみに限定したインストールポリシーの適用、ドライバーインストールイベントのリアルタイム監視、SharePointなど公開サーバーへの迅速なパッチ適用、カーネル整合性の監視などが挙げられる。

BYOVDはランサムウェアグループ間でのツール共有と組み合わさって急速に普及しており、企業のセキュリティ検知基盤そのものを無力化するアプローチが標準的な攻撃戦術として確立されつつある。防御側には、エンドポイント保護のレイヤーをカーネル監視・ドライバーガバナンスまで拡張する取り組みが求められている。
