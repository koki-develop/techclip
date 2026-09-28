---
date: "2026-09-28T18:22:02+09:00"
title: "ShinyHunters、「%50」の1文字エンコードでWAFを回避しOracle PeopleSoftを再び大規模攻撃"
description: "恐喝集団ShinyHunters(UNC6240)がURLエンコードを使ったWAFバイパス手法でOracle PeopleSoftの脆弱性CVE-2026-35273を再び大規模に悪用し、世界各地にWebシェルとバックドアを設置していることをGoogle Mandiantが報告した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/attackers-bypass-wafs-to-exploit-oracle.html"
  - "https://www.bleepingcomputer.com/news/security/shinyhunters-uses-waf-bypass-trick-in-oracle-peoplesoft-attacks/"
  - "https://cloud.google.com/blog/topics/threat-intelligence/shinyhunters-renewed-mass-exploitation-campaign-targeting-oracle-peoplesoft"
---

## 概要

Google傘下のMandiantとGoogle Threat Intelligence Group(GTIG)は9月25日、恐喝集団ShinyHunters(GoogleはUNC6240として追跡)がOracle PeopleSoftの脆弱性CVE-2026-35273を悪用する大規模な再攻撃キャンペーンを展開していると報告した。この脆弱性はEnvironment Management Hub(PSEMHUB)に存在するJavaデシリアライゼーションの欠陥で、認証なしのリモートコード実行が可能となる深刻なもの(CVSSスコア9.8)。今年6月に学術機関を狙ったゼロデイ攻撃として初めて悪用が確認され、Oracleはアウトオブバンドでパッチを公開していたが、パッチを適用せずWAFルールのみで対処していた組織が新たな攻撃の標的となっている。

## WAFバイパスの手口

今回のキャンペーンで注目されるのは、攻撃者が編み出した単純ながら効果的なWAFバイパス技術だ。脆弱なエンドポイントは`/PSEMHUB/`だが、攻撃者は先頭の「P」をURLエンコードした`%50`に置き換え、`/%50SEMHUB/`というリクエストパスでアクセスする。多くのWAFやリバースプロキシはURLデコード前の文字列でルールをマッチングするため、`/PSEMHUB/`をブロックするルールがこのエンコード済みバリアントを見逃してしまう。一方、Oracle WebLogicはリクエストをデコードしてからルーティングするため、脆弱なハンドラーに到達してしまう。Mandiantは、この回避技術がWAFルールなど公開済みの防御策への適応として編み出された点を指摘している。

## 攻撃チェーンと展開されるツール

攻撃者はまず`/%50SEMHUB/hub`へ5~15件のPOSTリクエストでシリアライズ済みJavaオブジェクトを送り、ファイルを書き込まずにOS情報を取得して脆弱性の有無を確認する。標的が確認されると、PSEMHUB.warディレクトリにJSP製のWebシェル「x.jsp」「u.jsp」(環境によっては「u2.jsp」)を設置する。x.jspは16進エンコードしたコマンドをPOSTパラメータ経由で受け取りWindows/Linuxを自動判別して実行するクロスプラットフォームシェル、u.jspは150KB単位のチャンクでBase64データをアップロードし大型バイナリを組み立てるためのシェルだ。Windows環境ではメディアプレイヤーを装った「Ple64.exe」を投下し、VMProtectで保護されたローダーを経てSIDEEYEと呼ばれるC++バックドアをメモリ上にロード、認証情報窃取や横展開、リバースプロキシ機能を持つこのバックドアは162.219.30[.]165のC2サーバーと通信する。Linux環境ではMeshAgentを永続化ツールとして展開し、Microsoftのサービスを装った偽ドメイン(azurenetfiles.netなど)を利用するほか、内部ネットワークへのトンネリングにNeo-reGeorgも使われている。実行されたコマンドの約25%はroot権限またはNT Authority\SYSTEM権限で行われており、侵害の深刻さを裏付けている。

## 被害状況と対策

攻撃は高等教育、技術・ITサービス、医療、農業、運輸、政府機関など幅広いセクターの数十システムに及び、地理的にも世界規模で確認されている。ShinyHuntersは窃取したデータを公開すると脅して金銭を要求する「データ盗難・恐喝」型の手口で知られ、同時期にFBIJobs.govポータルへの侵入で2~3TBの機密データを窃取したとも報じられている。Mandiantは、WAFルールの追加はパッチ適用の代替にはならないと強調し、CVE-2026-35273への緊急パッチ適用、マルチサーバ構成でのEMHubサービス無効化(シングルサーバ構成ではPSEMHUBアプリケーションの削除)、WebLogicログでの「/%50」など、PSEMHUBのパーセントエンコード済みバリアントを含むリクエストの検索、PSEMHUB.warディレクトリ配下の不審なファイルの点検、データベース監査ログでの大量クエリの監視、サービスアカウントやデータベース接続情報のローテーションなどを推奨している。単純な1文字のURLエンコードでセキュリティ製品をすり抜けられたという事実は、WAFなど単一の防御層に依存することの危険性を改めて浮き彫りにしている。
