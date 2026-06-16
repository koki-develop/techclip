---
date: "2026-06-17T03:34:32+09:00"
title: "Awesome MotiveのCDN侵害でWordPressプラグイン3本にバックドア、120万サイトに影響"
description: "OptinMonster・TrustPulse・PushEngageのCDN配信JavaScriptが改ざんされ、管理者セッションを悪用して不正アカウント作成とバックドア設置が行われるサプライチェーン攻撃が発覚した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/optinmonster-wordpress-plugin-hacked-in-cdn-supply-chain-attack/"
  - "https://patchstack.com/articles/supply-chain-attack-on-optinmonster-trustpulse-and-pushengage-tampered-cdn-scripts-auto-creating-rogue-admins/"
  - "https://securityaffairs.com/193616/malware/supply-chain-attack-hits-popular-wordpress-plugins-through-awesome-motive-cdn.html"
  - "https://www.infosecurity-magazine.com/news/wordpress-plugin-supply-chain/"
---

## 概要

2026年6月12〜14日にかけて、WordPressプラグインベンダーAwesome Motiveが運営するコンテンツデリバリーネットワーク（CDN）が侵害され、同社の主要プラグイン3本のJavaScriptファイルに悪意あるコードが埋め込まれた。影響を受けたのはOptinMonster（100万以上のサイトで使用）、TrustPulse、PushEngageで、合計120万サイト以上が潜在的な脅威にさらされた。セキュリティ企業Sansecが6月13日に侵害を発見し、OptinMonsterとTrustPulseのCDNスクリプトは6月12日22:42 UTCに除去され、PushEngageは6月14日までに対応が行われた。

## 侵害の経緯と攻撃手法

攻撃者はまず、Awesome Motiveのマーケティングウェブサイト上で稼働していた**UpdraftPlusプラグインの既知の脆弱性**を悪用してサーバーへのアクセスを取得した。そのサーバーは本番環境とは分離されていたものの、CDNアカウントのAPIキーが保存されており、攻撃者はこれを窃取して以下のCDNファイルを直接改ざんした：

- `a.omappapi.com/app/js/api.min.js`（OptinMonster）
- `a.opmnstr.com/app/js/api.min.js`（OptinMonster）
- `a.trstplse.com/app/js/api.min.js`（TrustPulse）
- `clientcdn.pushengage.com/sdks/pushengage-web-sdk.js`（PushEngage）

改ざんされたスクリプトは高度な検出回避機能を備えており、ヘッドレスブラウザやWebDriverの検出を避けるロジックを持ち、さらにlocalStorageに24時間のタイムスタンプを書き込んで同一サイトでの再実行を抑制した。**ログイン状態のWordPress管理者がサイトを訪問した場合にのみ**コードが起動するという巧妙な設計で、一般ユーザーには無害に見える構造になっていた。

## 不正管理者アカウント作成とバックドア設置の仕組み

スクリプトが起動すると、管理者のセッションを利用してREST APIおよびAJAXエンドポイントから認証トークンとnonceを収集した。その後、以下の4つの経路を試みて不正な管理者アカウントを作成した：

1. REST API（`/wp-json/wp/v2/users`）
2. 管理フォーム（`/wp-admin/user-new.php`）
3. WordPress AJAX
4. 隠しiframe

作成されるアカウントは固定型（`developer_api1` / `customer1usx@gmail.com`）とランダム型（`dev_xxxxxx` / `dev_xxxxxx@gmail.com`）の2パターンがあった。Patchstackの観測では、36時間で81のIPアドレスから271件の不正リクエストが検出されており、そのうち267件がランダム型のアカウント名を使用していた。

管理者アカウント取得後は、ZIPファイル形式のバックドアを`/wp-admin/update.php?action=upload-plugin`経由でアップロードし、「Content Delivery Helper」または「Database Optimizer」という無害に見える名称のプラグインとしてインストールした。このバックドアはウェブシェルや任意のPHP実行機能を備えており、攻撃者に完全なリモートアクセス権限を与えた。収集したデータはXOR暗号化（鍵：`jX9kM2nP4qR6sT8v`）でエンコードされ、正規サービスのtidio.comを模倣して4月28日に登録されたC2ドメイン`tidio.cc`（IP: 84.201.6.54）へ送信された。

## 影響範囲と対応状況

OptinMonsterとTrustPulseへの悪意あるコード注入は6月12日22:17 UTCから始まり、わずか25分後の22:42 UTCには除去された。一方、PushEngageは6月14日まで侵害された状態が続いた。Awesome Motiveの他製品（WPForms：600万インストール、All in One SEO：300万インストール、MonsterInsights：200万インストール）への侵害は現時点では確認されていないが、警戒が必要な状況にある。

影響を受けた可能性のあるサイト管理者は以下の対応が推奨される：

- `developer_api1`または`dev_xxxxxx`形式の不審な管理者アカウントを削除
- `wp-content/plugins`ディレクトリをファイルシステム上で直接検査し、隠しプラグインを確認
- サーバーサイドのマルウェアスキャンを実施
- すべての認証情報とセキュリティソルトをローテーション
- C2ドメイン`tidio.cc`をブロック

なお、サイトのダッシュボードからは隠しプラグインが見えないよう細工されている可能性があるため、ファイルシステムを直接確認することが重要だ。

## サプライチェーン攻撃としての教訓

今回の攻撃は、自身のWordPressサイトが完全にパッチ済みであっても、利用しているプラグインのCDNが侵害された場合にはなす術がないことを示している。攻撃コードはプラグインの配布サーバーではなくCDNファイルに直接埋め込まれており、標準的なファイル整合性チェックでは検出が困難だった。セキュリティ研究者は、CDNを経由したサプライチェーン攻撃に対してはサードパーティリソースの継続的な監視と、ウェブアプリケーションファイアウォール（WAF）による異常なAPI呼び出しの検出が有効な対策であると指摘している。
