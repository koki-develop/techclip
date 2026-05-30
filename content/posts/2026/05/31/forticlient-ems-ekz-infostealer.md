---
date: "2026-05-31T02:28:18+09:00"
title: "FortiClient EMS認証バイパス脆弱性（CVE-2026-35616）を悪用したEKZ情報窃取マルウェアが企業端末を標的に"
description: "脅威アクターがFortiClient EMSのCVSS 9.1の認証バイパス脆弱性を悪用し、正規パッチに偽装したEKZ情報窃取マルウェアをPowerShell経由で配布していることが確認された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/hackers-exploit-forticlient-ems-flaw-to-push-infostealer-malware/"
  - "https://www.helpnetsecurity.com/2026/05/29/forticlient-ems-vulnerability-infostealer/"
---

## 概要

FortiClient Enterprise Management Server（EMS）に存在するCVSS 9.1の重大な認証バイパス脆弱性（CVE-2026-35616）を悪用した攻撃が確認された。脅威アクターはこの脆弱性を通じてEMS設定やVPNポリシーを無断で改ざんし、Fortinetの正規パッチに偽装した情報窃取マルウェア「EKZ」をエンドポイントへ展開している。Fortinetは4月上旬にバージョン7.4.5および7.4.6向けの緊急パッチを公開しており、CISAも連邦機関に対して即時適用を義務付けた。The Shadowserver Foundationの調査では、インターネットに公開されたEMSインスタンスが約2,000件確認されている。

## 攻撃チェーンの詳細

攻撃は複数段階で構成されている。まず脆弱性を悪用してエンドポイントAPIへの未認証アクセスを行い、管理者権限に相当する操作を実行する。次にリモートアクセスプロファイルおよびVPNポリシーを改ざんして悪意のあるスクリプトを埋め込む。エンドポイントがIPsecトンネルを確立すると、正規の`fortitray.exe`がコマンドプロンプト経由でバッチスクリプトを起動し、Base64エンコードされたPowerShellペイロードを実行する。このペイロードはFortinetの公式パッチに偽装されており、被害者が気づきにくい構造になっている。窃取されたデータはHTTP経由で攻撃者が管理するVPSサーバへ送信される。

## EKZマルウェアの機能と影響

EKZはMinGWでコンパイルされた情報窃取マルウェアで、ChromiumおよびGeckoエンジンを採用するブラウザ（Chrome、Firefox、Torブラウザなど）を標的とする。収集する情報はブラウザに保存された認証情報・パスワード、クレジットカード情報、住所・電話番号などのオートフィルデータ、セッションクッキーと多岐にわたる。特にクッキーの窃取はMFAを回避した不正ログインを可能にするため、侵害の影響が拡大するリスクがある。データ送信後はローカルの痕跡を消去する機能も備えており、検知回避への配慮がなされている。

## 検知と対策

防御側は以下の指標を監視することが推奨される。EMSログにおける「Certificate not found in request header」のエラーエントリや証明書認証の異常、見覚えのないIPアドレス（Torや外部VPSなど）からの管理操作、およびリモートアクセスプロファイルの予期しない変更が主要な検知シグナルとなる。すでに侵害が疑われる組織では、影響を受けたサービス全体でのパスワード変更、既存セッションの強制無効化、および保存された金融情報への不正利用がないかの確認が必要とされる。FortiClient EMSを運用しているすべての組織は、速やかにパッチを適用し、設定変更の監査ログを精査することが強く求められる。
