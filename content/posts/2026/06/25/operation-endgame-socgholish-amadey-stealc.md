---
date: "2026-06-25T02:42:08+09:00"
title: "国際共同作戦「Operation Endgame」がSocGholish・Amadey・StealCのインフラを解体、2,700万件の認証情報と4,700万ドルの暗号資産を回収"
description: "オランダ・米国など8カ国の法執行機関とMicrosoft・ESET・Bitdefenderが連携した「Operation Endgame」の拡大作戦が、3種のマルウェアインフラを一斉解体し、326台のサーバーと142ドメインを無効化した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/operation-endgame-disrupts-socgholish.html"
  - "https://www.bleepingcomputer.com/news/security/law-enforcement-nukes-socgholish-malware-from-nearly-15-000-sites/"
  - "https://thehackernews.com/2026/06/amadey-and-stealc-malware-network.html"
  - "https://www.europol.europa.eu/media-press/newsroom/news/global-cyber-strike-disrupts-socgholish-amadey-and-stealc-malware-networks"
---

## 概要

オランダ・カナダ・ドイツ・米国・ベルギー・デンマーク・フランス・英国の法執行機関と、Microsoft・Bitdefender・Bitsight・ESETなどの民間企業が連携した国際共同作戦「Operation Endgame」の拡大フェーズが完了した。今回の作戦ではSocGholish（FakeUpdates）、Amadey、StealCの3種のマルウェアインフラを同時に解体し、326台のサーバーと142ドメインを無効化。感染したWordPressサイト約15,000件を修復するとともに、2,700万件の盗まれたログイン情報と4,700万ドル相当の暗号資産を回収した。2026年5月時点で全世界の感染コンピューターは14万台以上に上っており、Microsoftだけで1万8,000台以上の被害端末を特定・修復したという。

## 解体されたマルウェアの技術的詳細

**SocGholish（FakeUpdates/GhoLoader）**は2017年以来活動するJavaScriptベースのダウンローダーで、主にWordPressサイトに悪意あるコードを注入し、正規のブラウザアップデートに偽装してユーザーにマルウェアをダウンロードさせる手法を用いる。DNSプロバイダーへの不正アクセスで正規ドメインの配下に悪意あるサブドメインを作成する「ドメインシャドーイング」技術も活用しており、Evil Corp（2007年から活動するロシアのサイバー犯罪組織）をはじめLockBit・RansomHubとの関連も確認されている。今回の作戦では106台のサーバーを停止し、感染サイト14,971件を直接クリーンアップした。

**Amadey**は2018年10月から稼働するC++製モジュラー型バックドアで、最新バージョンは5.87。マルウェア・アズ・ア・サービス（MaaS）モデルで1ライセンス600ドル・リビルドごとに50ドルで販売されており、53の異なるボットネットクラスターから配布される。システム情報収集・ファイルダウンロード・スクリーンショット取得・SOCKS proxy・VNCセッション・クリップボード監視・RDP有効化など多機能な攻撃能力を持ち、LummaやVidar・RedLineなどの情報窃取マルウェアの二次配布にも利用されていた。

**StealC**は2023年1月に初登場した情報窃取特化型マルウェアで、最新バージョンは2.2.1（2026年6月時点）。月300ドルまたは6か月1,000ドルのサブスクリプション制で提供され、認証情報・Cookie・オートフィルデータ・クレジットカード情報・閲覧履歴を幅広く窃取する。

## 背景と今後の展望

Operation Endgameは2024年に発足した継続的な国際サイバー犯罪対策の枠組みで、今回はその拡大フェーズとして位置づけられる。Infobloxの調査によれば、2026年に入ってクラウド顧客の55%がSocGholishのインフラへの到達を試みるトラフィックを記録しており、これらのマルウェアが広範かつ活発に利用されていた実態が浮き彫りになった。オランダ国家ハイテク犯罪ユニットのMaikel Rollman氏は「この作戦により、サイバー犯罪者が感染したコンピューターシステムへアクセスする手段を剥奪した」と述べた。今回の作戦で200件を超えるC2ドメインとIPアドレスがブラックリスト登録され、当局はWordPressサイト管理者に対してパスワード変更・多要素認証の有効化・不審なアカウントの削除・ソフトウェアの最新化を推奨している。
