---
date: "2026-05-02T02:27:28+09:00"
title: "CORDIAL SPIDERとSNARKY SPIDER：ビッシングとSSO悪用で1時間以内に恐喝するSaaS攻撃の実態"
description: "CrowdStrikeが新興サイバー犯罪グループCORDIAL SPIDERとSNARKY SPIDERを特定。ビッシングとSSO偽装でSaaSへ不正侵入し、短時間でデータを窃取・恐喝する手口が明らかになった。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/05/cybercrime-groups-using-vishing-and-sso.html"
  - "https://cyberscoop.com/crowdstrike-cordial-spider-snarky-spider-extortion-attacks/"
  - "https://www.crowdstrike.com/en-us/blog/defending-against-cordial-spider-and-snarky-spider-with-falcon-shield/"
---

## 概要

CrowdStrikeは2026年4月末、**CORDIAL SPIDER**（別名：BlackFile、CL-CRI-1116、UNC6671）と**SNARKY SPIDER**（別名：UNC6661）という2つの新興サイバー犯罪グループを特定し、警告を発した。両グループは少なくとも2025年10月から活動しており、Scattered Spiderが確立した手口を踏襲しながら、ビッシング（音声フィッシング）とシングルサインオン（SSO）の悪用を組み合わせたSaaS環境への迅速な侵入・恐喝攻撃を展開している。主に英語話者で構成され、Thecomと呼ばれるサイバー犯罪エコシステムとの関連が指摘されている。標的はアメリカの小売・ホスピタリティ・航空・金融・法律・テクノロジー企業など多岐にわたる。

## 攻撃の手口：侵入から恐喝まで

攻撃の流れはいくつかのフェーズに分かれる。まず攻撃者はITサポートを装った電話・SMS・メールで標的の従業員に接触し（ビッシング）、企業のSSO/IdPポータルを模倣した**Adversary-in-the-Middle（AiTM）フィッシングページ**へ誘導する。被害者が認証情報を入力すると、攻撃者はリアルタイムで資格情報とMFAセッショントークンを窃取する。

侵入後は、攻撃者制御のMFAデバイスを登録して既存デバイスを削除し、永続的なアクセスを確保する。SNARKY SPIDERはGenymobile製Androidエミュレータを、CORDIAL SPIDERは実モバイルデバイスとQEMUを使い分けている点が特徴的だ。さらにSNARKY SPIDERは「alert」「incident」「MFA」といったセキュリティ関連キーワードをフィルタリングするメール受信ルールを設定し、不審なアクティビティの通知を被害者から隠蔽する。その後、内部の従業員ディレクトリをスクレイピングして高権限アカウントを特定し、Google Workspace・HubSpot・Microsoft SharePoint・Salesforceから「confidential」「SSN」「contracts」「VPN」といったキーワードで機密ファイルを検索・大量ダウンロードする。**SNARKY SPIDERは侵入から1時間以内にデータ窃取を開始する**ケースも確認されており、対応の迅速さが際立っている。

## インフラと恐喝戦術

地理的な追跡を回避するため、両グループはMullvad・Oxylabs・NetNut・9Proxy・Infatica・NSOCKSといった商用VPNサービスや住宅用プロキシネットワークを駆使し、IPベースの評判フィルタをすり抜ける。Scattered Spiderと比較すると技術的な洗練度は低いが、同等の社会工学的手法を用いることで高い成功率を維持している。

恐喝の要求額は**7桁（100万ドル以上）**に達するケースもあり、要求に応じない被害者はDDoS攻撃の対象となる。さらにSNARKY SPIDERは、従業員へのスワッティング（偽の緊急通報）といったより攻撃的な嫌がらせ戦術を用いることが報告されている。CORDIAL SPIDERが運営するデータリークサイト「BlackFile」は2026年4月29日時点でオフラインだったとされるが、活動自体は継続しているとみられる。

## 防御と推奨対策

CrowdStrikeはFalcon Shieldによる3つの検知機能（SaaS専門知識・高度な異常検知・ネットワークインテリジェンス分析）を防御策として提示している。組織側の対策としては、デバイス登録だけに依存しない多要素認証の強化、不審なメール受信ルール変更の監視、そしてSaaS環境における迅速な横移動パターンを検出する体制の整備が重要だ。特にIDプロバイダー（IdP）はすべてのSaaSアプリへのシングルポイントとして機能するため、その保護が最優先事項となる。
