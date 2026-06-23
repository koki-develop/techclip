---
date: "2026-06-24T02:40:18+09:00"
title: "WhatsApp経由のVBScriptキャンペーン、ManageEngine RMMを悪用して遠隔操作を確立"
description: "KasperskyがWhatsApp経由で偽ビジネス文書に見せかけたVBScriptを配布し、正規のManageEngine RMMツールをインストールして遠隔操作を行うマルウェアキャンペーンを発見した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/whatsapp-vbscript-campaign-uses-fake.html"
  - "https://securelist.com/whatsapp-vbs-rmm-campaign/120290/"
  - "https://www.bleepingcomputer.com/news/security/whatsapp-phishing-attack-uses-fake-business-docs-to-hack-pcs/"
---

## 概要

Kasperskyの研究者が、WhatsAppを介して悪意のあるVBScriptファイルを配布するマルウェアキャンペーンを発見した。攻撃者はまずWhatsAppアカウントを侵害し、被害者の連絡先リストにある人物に対して偽のビジネス文書を送り付ける。ファイルは「Financial Reports.vbs」「Account Statement.vbs」「Outstanding Payment List.vbs」といった名称で、請求書や債務通知・銀行明細書を装っている。メッセージが既知の連絡先から届くように見えるため、被害者は疑わずにファイルを開いてしまう。文書名はポルトガル語・フランス語・ドイツ語・マレー語など複数言語で作成されており、マレーシア・ブラジル・インド・メキシコ・シンガポール・英国・スペイン・台湾・オーストラリア・ロシア・ベトナムを含む世界10カ国以上のユーザーが標的となっている。特にマレーシアが被害の約80%を占めている。

## 多段階の感染チェーン

攻撃は複数のステージで構成される巧妙な感染チェーンを採用している。まず初期のVBScriptがWindows Script Host（WScript.exe）によって実行され、`C:\Users\Public\Documents\` 配下に `Temp_<ランダム文字列>` という名前の隠しワークディレクトリを作成する。次にcurl・bitsadmin・certutil・PowerShellのいずれかを使って攻撃者のインフラから2つの追加スクリプトをダウンロードする。

2つ目のスクリプトはWindowsのUAC（ユーザーアカウント制御）設定をレジストリで改ざんし、`ConsentPromptBehaviorAdmin` の値を0に設定することで管理者操作の確認ダイアログを無効化する。その後、ManageEngine Endpoint Centralの展開パッケージを含むZIPアーカイブをダウンロードし、`setup1.vbs` が正規のEndpoint Centralエージェントをサイレントインストールする。インストールされたRMMソフトウェアは攻撃者が管理するサーバーに接続するよう設定されており、これにより攻撃者は被害者のマシンに対する永続的なリモート管理権限を獲得する。スクリプト内には大量の難読化・ジャンクコード・文字列連結・偽のWindows Updateコメントが含まれており、セキュリティソフトによる検知を回避するよう設計されている。

## 正規ツールの悪用とLiving-off-the-Land戦術

このキャンペーンの特徴は、マルウェアを直接配布するのではなく、ManageEngine Endpoint Centralという正規のIT管理ツールを遠隔操作の手段として悪用する点にある。正規のRMMソフトウェアはセキュリティソフトのホワイトリストに登録されていることが多く、悪意のある通信として検出されにくい。攻撃者の目標は、データ窃取・ラテラルムーブメント（横展開）・さらなるネットワーク侵害など、継続的なアクセスを通じた多様な攻撃活動の実施と見られる。

## 攻撃インフラと帰属

確認された攻撃者のインフラには、`temu.baskwms[.]top`・`invoice.msopsa[.]top`・`qse.shoppes[.]help` などのドメインや、C2サーバーIPアドレス `202.61.160[.]201`・`202.61.160[.]202`・`38.55.151[.]63` が含まれる。ファイルの配信にはAliyun OSS・AWS S3・Backblaze B2などのクラウドストレージも利用されている。複数のVBSバリアントが記録されており、キャンペーンが活発に続いていることを示している。

帰属については、スクリプト内に中国語（簡体字）のコメントが埋め込まれていること、ValleyRATやGh0st RATとのインフラの重複が確認されていることから、中国語話者の攻撃者が関与している可能性が低〜中程度で示唆されている。ただし確定的な帰属には至っておらず、研究者らは引き続き調査中としている。本キャンペーンは2026年6月時点でも活動中であり、ユーザーには見覚えのない実行ファイルやスクリプトファイルの開封を避けるよう注意が呼びかけられている。
