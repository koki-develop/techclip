---
date: "2026-10-11T08:12:04+09:00"
title: "AhsayCBSの未修正脆弱性を連鎖悪用、XMRigマイナーがMicrosoft Edgeに偽装して侵入"
description: "セキュリティ企業Huntressは、バックアップ製品AhsayCBSの未修正の認証バイパスとコマンドインジェクションを連鎖させた攻撃で、Webシェル設置とMicrosoft Edge偽装のXMRigマイナー展開が行われていることを確認した。"
tags:
  - Security
references:
  - "https://www.huntress.com/blog/ahsaycbs-flaws-exploit"
  - "https://www.securityweek.com/unpatched-ahsaycbs-vulnerabilities-exploited-in-the-wild/"
  - "https://thehackernews.com/2026/10/attackers-exploit-ahsaycbs-flaws-to.html"
---

## 概要

セキュリティ企業Huntressは、バックアップ製品AhsayCBSに存在する未パッチの脆弱性2件を連鎖させた攻撃が実環境で発生していることを確認した。悪用されているのは、`checkSysPwd`関数の認証チェック不備による認証バイパス「CVE-2026-105133」(CVSS 5.5)と、Replication Receiverコンポーネント(`/rps/api/json/UpdateReceivers.do`)に存在するコマンドインジェクション「CVE-2026-105134」(CVSS 9.3)である。攻撃者はまずCVE-2026-105133で認証ロジックを迂回し、続いてReplication Receiverコンポーネント自体が持つランダムトークンによる認証情報代替の欠陥であるCVE-2026-105134を悪用することで、NT AUTHORITY\SYSTEM権限での未認証リモートコード実行を達成する。10月7日23時20分(UTC)以降に悪用が始まり、10月8日時点で少なくとも5組織が標的となったことが確認されている。AhsayCBSはバージョン10.3.4までが影響を受けるが、執筆時点でパッチは提供されていない。

## 攻撃チェーンとペイロードの展開

悪用に成功した攻撃者は、悪意あるレシーバー設定を通じてJSP形式のWebシェルをアプリケーションの配信ディレクトリに埋め込み、以降の操作の足がかりとする。続いてAlibaba Cloud OSS上のバケット(`imagefiles-backup.oss-ap-southeast-7.aliyuncs.com`)からXMRigクリプトマイナーをダウンロードし展開する。このマイナーは実行ファイル名を`edge.exe`に改名することでMicrosoft Edgeブラウザに偽装し、プロセス一覧からの検出を回避する狙いがある。

## 検出回避と永続化の手口

永続化のために、攻撃者は正規のサービス管理ユーティリティNSSM(Non-Sucking Service Manager)の改変版を`msedge.exe`という名前で配置し、マイナーをWindowsサービスとして常駐させる。さらに`MicrosoftEdgeUpdateSvc`という名称の不正サービスを作成し、正規のEdgeUpdateサービスであるかのように偽装、SYSTEM権限での実行とクラッシュ時の自動再起動機能を持たせている。加えて、`Taskgmr.ps1`という名のPowerShellスクリプトが展開されており、タスクマネージャーの起動を監視してマイナーの動作を一時停止させ、18時の時点、あるいは夜間に1時間以上起動したままの場合にはタスクマネージャー自体を強制終了するなど、AI支援による開発が疑われる高度な検出回避ロジックを備えている点も報じられている。これらに加え、調査を免れるための追加のバックドアも一部の環境にインストールされていたという。

## 影響と推奨される対策

AhsayはJSONベースのAPIを公開するバックアップソフトウェアとして広く利用されており、今回のような未認証RCEと暗号資産マイニングの組み合わせは、計算リソースの悪用に留まらず、バックアップデータそのものへの不正アクセスや改竄のリスクも伴う。ベンダーからのパッチが未提供であるため、各社は当面の緩和策として、AhsayCBSの管理インターフェースへのアクセスを信頼できるIPアドレスのみに制限するか、VPN経由でのアクセスを必須とすることが強く推奨されている。また、侵害の兆候(`edge.exe`や`msedge.exe`という名の不審なプロセス、`MicrosoftEdgeUpdateSvc`サービスの存在など)が見つかった場合は、信頼できるバックアップからホスト全体を再イメージングすることが望ましいとされている。
