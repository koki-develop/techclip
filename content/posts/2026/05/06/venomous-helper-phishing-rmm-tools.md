---
date: "2026-05-06T02:38:47+09:00"
title: "正規RMMツールを二重に悪用するフィッシングキャンペーン「VENOMOUS#HELPER」、米国80以上の組織を標的"
description: "Securonixが追跡するVENOMOUS#HELPERキャンペーンは、SSAを装ったフィッシングメールを起点に、SimpleHelpとScreenConnectという2種類の正規RMMツールを同時展開し、米国を中心に80以上の組織への持続的なリモートアクセスを確立している。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/05/phishing-campaign-hits-80-orgs-using.html"
  - "https://www.securonix.com/blog/venomous-helper-phishing-campaign"
  - "https://www.infosecurity-magazine.com/news/ssa-emails-venomous-helper-phishing/"
---

## 概要

セキュリティ企業Securonixは、「VENOMOUS#HELPER」と命名されたフィッシングキャンペーンを追跡・公開した。2025年4月から活発化しているこのキャンペーンは、主に米国の80以上の組織を標的とし、正規のリモート監視・管理（RMM）ツールであるSimpleHelpとConnectWise ScreenConnectを同時に悪用して持続的なリモートアクセスを確立する点が特徴的だ。同キャンペーンはRed CanaryとSophosがSTAC6405として追跡している活動とも重複が確認されている。

攻撃の入口は、米社会保障局（SSA）を偽装したフィッシングメールだ。受信者に「メールアドレスの確認とSSA明細書のダウンロード」を促すリンクが含まれており、クリックするとメキシコの正規企業サイト（gruta.com.mx）が改ざんされた偽のSSA確認ページへ誘導される。メールのフィルタリングを回避するために侵害済みのメキシコ系ドメインを中継として利用しているのが巧妙な点だ。

## 感染の技術的メカニズム

被害者が偽ページ上でメールアドレスを送信すると、別の侵害済みホストへリダイレクトされ、悪意のある実行ファイル（`statement5648.exe`）がダウンロードされる。このファイルはJWrapperでパッケージングされており、Windowsのデフォルト動作（拡張子の非表示）とカスタムアイコンを悪用して政府ドキュメントに偽装する。さらに、SimpleHelp Ltd.によるThawteのAuthenticodeコード署名が有効なため、Windows SmartScreenの警告は「確認済みの発行元」を示す青いダイアログに変わり、ウイルス対策ソフトによる検出を回避する。

感染の連鎖は次の5段階で進行する。

1. JWrapperのブートストラップが、サポート切れのOracle Java 1.7.0_79（2015年EOL）を`C:\ProgramData\JWrapper-Remote Access\`に展開する
2. `SimpleService.exe`が「Remote Access Service」という名前でWindowsサービスとして登録され、SafeBootレジストリキーへの書き込みによりセーフモード再起動後も生存する
3. `SimpleGatewayService.exe`が特殊なJVMフラグ（`-Xrs`、TLSダウングレード設定）でJavaランタイムを起動する
4. `session_win.exe`（winlogon.exeからのトークン窃取）と`elev_win.exe`（UACバイパス）によりセッションが昇格する
5. 2系統のC2チャネルが同時に確立される

## デュアルRMMによる冗長的バックドア

このキャンペーンの最大の特徴は、2種類のRMMツールを同時に展開する「冗長デュアルチャネル方式」だ。一方のチャネルが検出・遮断されても、もう一方で攻撃継続を確保する設計になっている。

- **SimpleHelp 5.0.1**：`84.200.205[.]233:5555`に設置された攻撃者自身のサーバーに接続。自動監視、スクリプトによるコマンド実行、ファイル転送機能を提供する
- **ConnectWise ScreenConnect**：`213.136.71.246:8041`のリレーサーバー（ドメイン：`sslzeromail[.]run.place`）経由でインタラクティブなデスクトップアクセスを提供するセカンダリチャネルとして機能する

また、マルウェアは3つの監視ループをバックグラウンドで並行実行し、毎時986件ものプロセス生成イベントをオペレーターの操作なしに発生させる。WiFiインターフェースの監視（約15秒間隔）、マウス位置によるユーザー在席確認（約23秒間隔）、WMIを用いたセキュリティ製品のスキャン（約67秒間隔）がその内容だ。

## EDR回避と永続化の手口

EDRの検出を回避する工夫として、`wmic.exe`を`wmic.exe.bak`にリネームして`C:\Windows\System32\wbem\`に配置し、名前ベースの検出ルールをすり抜けつつ同一のWMIクエリ（SecurityCenter2）を実行するという手口が確認されている。このリネームされたバイナリはホスト側の高信頼度の侵害指標となる。

永続化においては、Windowsサービスとしてのインストールに加え、強制終了されても自動再起動するウォッチドッグ機構が組み込まれており、`C:\ProgramData\JWrapper-Remote Access\JWAppsSharedConfig\sgalive`ファイルをリバイバルシグナルとして使用する。

## 帰属と推奨対策

Securonixは現時点でこのキャンペーンを既知の脅威アクターに帰属していないが、「西側経済圏を標的とする金銭的動機を持つIAB（初期アクセスブローカー）またはランサムウェアの前段階作戦」と評価している。

防御の観点からは、名前ベースの検出に頼らず、異常なプロセス系譜、定期的な自動ポーリングパターン、標準外のサービスインストールをホストテレメトリで監視する行動分析が有効とされる。特に、オペレーターが活動開始した際に自動監視ループに重なって発生する`whoami`・`ipconfig`・`net user`・`systeminfo`といった即時状況確認コマンドの連続実行を検出することが重要だ。
