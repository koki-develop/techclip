---
date: "2026-09-19T08:11:18+09:00"
title: "Microsoft、パスキー偽装フィッシングでMicrosoft 365アカウント乗っ取り多発と警告 SharePointやOneDriveから機密データ窃取"
description: "MicrosoftはIT部門を装いパスキーやMFA設定の更新を持ちかけるフィッシング攻撃が相次ぎ、Microsoft 365アカウントの乗っ取りとSharePoint・OneDrive・Exchange Onlineからのデータ窃取につながっていると警告した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/attackers-use-passkey-phishing-to.html"
  - "https://www.channelinsider.com/security/news-microsoft-passkey-phishing-365/"
  - "https://redmondmag.com/articles/2026/09/16/microsoft-warns-passkey-phishing-attacks-are-leading-to-cloud-account-takeovers.aspx"
---

## 概要

Microsoftは、IT部門を装った電話連絡やSMSを起点に、パスキーやMFA(多要素認証)の設定更新を持ちかけるソーシャルエンジニアリングによって、Microsoft 365クラウドアカウントが乗っ取られる被害が相次いでいると警告した。攻撃は2026年5月ごろから観測されており、Microsoftは9月9日に詳細な脅威分析を公表した。標的となった組織では、攻撃者がSharePoint Online・OneDrive・Exchange Onlineから機密データを数時間から数日にわたって窃取するケースが確認されている。

## 攻撃の手口

攻撃者はまずIT部門のヘルプデスクを装って従業員に電話をかけ、SMS経由で偽の認証ページへ誘導する。ここでAiTM(Adversary-in-the-Middle)フィッシングにより認証情報やセッショントークンを窃取するほか、デバイスコード認証フローを悪用し、正規のログイン画面を介さずに攻撃者側のセッションを承認させる手口も用いられている。侵入に成功すると、攻撃者は自ら電話番号や認証アプリをMFA手段として追加登録し、当初の窃取した認証情報に依存しない永続的なアクセス経路を確保する。この手法により、強固なはずの多要素認証やパスキーによる保護も、従業員が「相手は正規のIT部門だ」と信じ込んだ時点で無力化されてしまう。確認された悪性ドメインにはpasskeyhelpdesk[.]com、secure-passkey[.]com、setupmypasskey[.]com、integratedsso[.]com、oktasession[.]comなどがある。

## 侵入後の挙動と攻撃者の実態

アカウントの制御を奪った後、攻撃者はMicrosoft Graph APIを多用してユーザー・グループ・権限情報を大量に照会し、標的組織内の偵察を行う。その後、SharePoint OnlineやOneDriveからのファイルダウンロード、REST API経由のメールボックス収集などを通じてデータを窃取する。Microsoftによれば、認証・偵察・窃取の各段階で異なるインフラを使い分けるなど、攻撃者側は個々のAPIリクエストでは検知されにくいよう行動を分散させているという。Microsoftは「Graphのアクティビティは個々のAPIリクエスト単位ではなく、行動の推移やイベント間の相関を含めて総合的に評価する必要がある」と指摘する。同社はこの一連の活動をStorm-3121およびStorm-3032として追跡しており、Cordial SpiderやUNC6671など複数のサイバー犯罪集団との重複も確認されている。これらの集団はShinyHunters、Falcon、Helixといった複数の恐喝ブランドを使い分けつつ、フィッシング基盤を共有している可能性があるとみられる。

## 対策

Microsoftは、パスキーやMFA、シングルサインオンの設定更新を求める連絡を受けた場合は、社内の別経路で独立して真偽を確認するよう利用者に呼びかけている。組織向けには、不要であればデバイスコード認証や認証情報の転送フローをブロックすること、不審なサインインやMFA登録を継続的に監査し疑わしい認証手段を速やかに削除すること、パスキーやWindows Hello for Businessなどフィッシング耐性の高いMFAを条件付きアクセスで強制すること、Exchange・SharePoint・Graph特権アプリへのアクセスに管理された準拠デバイスを要求することなどを推奨している。パスキーは本来フィッシング耐性の高い認証手段とされるが、今回の一連の攻撃は、技術的な認証強化だけでは対応しきれない、人間を標的にした社会工学的な脅威が依然として最大のリスクであることを改めて示している。
