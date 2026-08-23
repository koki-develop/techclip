---
date: "2026-08-23T14:07:39+09:00"
title: "Windows Defenderの正規ブート修復ドライバ「BTR.sys」がセキュリティソフト破壊の武器に転用可能と判明"
description: "Check Point ResearchがBlack Hat USA 2026で、Defenderの正規署名済みブート修復ドライバ「BTR.sys」を悪用し、起動時にセキュリティソフトそのものを削除できる手法「BTR Reforged」を発表した。"
tags:
  - Security
references:
  - "https://research.checkpoint.com/2026/btr-reforged-weaponizing-defenders-remediation-driver-as-a-kernel-operation-primitive/"
  - "https://thehackernews.com/2026/08/microsoft-defenders-own-driver-can-be.html"
  - "https://www.scworld.com/brief/researchers-find-way-to-weaponize-windows-defenders-own-driver"
---

## 概要

Check Point Researchは、Black Hat USA 2026およびDEF CON 34において、Windows Defenderに組み込まれた正規の署名済みドライバ「BTR.sys」（Boot-Time Removal、ブート時修復ドライバ）を悪用し、起動時にカーネルレベルで任意のファイル・レジストリ操作を実行できる手法「BTR Reforged」を発表した。BTR.sysは本来、ロックされたマルウェアコンポーネントなど再起動が必要なファイルを安全に削除するためにDefenderが利用する正規機能で、MpEngine.dllの「BOOTTIMETOOL」リソースとして埋め込まれ、Windows 7からWindows 11 25H2まで全バージョンに存在する。研究者らはこの機能のプロトコルをリバースエンジニアリングし、Defender自身のセキュリティバイナリ（WdFilter.sysやMsMpEng.exeなど）を削除できることを実証した。ゼロデイ脆弱性ではなく正規機能の悪用にあたるためCVEは付与されておらず、MSRCは緊急のサービス提供基準を満たさないと判断している。

## 技術的な詳細

BTR.sysの設定データはRC4ストリーム暗号（ハードコードされた256バイトの共通鍵）で保護され、修正版CRC-32で整合性が検証された上でAlternate Data Stream（ADS）に格納される。この鍵は少なくとも18種類確認されている64ビット署名済みバージョンすべてで共通しているため、研究者らは概念実証ツール「BTR_CLI」を用いてドライバを抽出し、暗号化された操作トランザクションを独自に構築できることを示した。この手法により、ファイル・ディレクトリの削除や移動、レジストリキー・値の削除や任意の値の書き込みといった操作をカーネルモード（Ring 0）から実行可能になる。特に危険視されているのが「Golden Window」と呼ばれるタイミングで、ドライバを「Boot Bus Extender」グループでStart=1（System起動時）に設定すると、ファイルシステムは書き込み可能な状態になっている一方でセキュリティサービスはまだ起動していない隙間が生じ、この間にDefender自身を含むセキュリティ製品のバイナリを削除できてしまう。悪用には管理者権限とSeLoadDriverPrivilegeが必要なため、いわゆる「LOLDriver」（環境寄生型ドライバ)の一種として分類される。

## Microsoftの対応と検出策

MSRCはこの手法について、悪用に管理者権限を要することを理由に「即時のサービス提供基準を満たさない」と判断した。研究者が公開した概念実証ツール「BTR_CLI」のGitHubリポジトリには「パッチ予定なし」との記載があるが、これはMicrosoftが公式に確認した内容ではない。今のところ実際の攻撃での悪用は報告されていない。防御側の対策としては、ADS（代替データストリーム)の作成監視（SysmonのイベントID 15）、System（PID 4）プロセスによる想定外のファイル削除の監視、不審なドライバロードのコンテキスト分析などが有効とされる。研究者らは、この事例が事件対応調査の過程で偶然発見されたと説明しており、信頼されているセキュリティ基盤コンポーネント自体が、意図せず攻撃者に悪用されうるカーネル操作のプリミティブになり得ることを示す事例として注目されている。
