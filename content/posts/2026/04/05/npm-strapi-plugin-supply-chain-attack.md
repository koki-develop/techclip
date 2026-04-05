---
date: "2026-04-05T18:12:10+09:00"
title: "Strapiプラグイン偽装の悪意あるnpmパッケージ36件、暗号資産企業を標的にC2エージェントを展開"
description: "Strapi CMSプラグインを装った36個の悪意あるnpmパッケージが発見され、RedisのRCEやDockerコンテナ脱出、永続的なC2エージェント展開といった高度な攻撃機能を持つサプライチェーン攻撃であることが明らかになった。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/04/36-malicious-npm-packages-exploited.html"
  - "https://safedep.io/malicious-npm-strapi-plugin-events-c2-agent/"
  - "https://dev.to/kornilovconstru/malicious-npm-packages-disguised-as-strapi-plugins-enable-data-exfiltration-and-remote-code-5bb0"
---

## 概要

2026年4月初旬、セキュリティ研究者はnpmレジストリに公開された36個の悪意あるパッケージを発見した。これらはすべて `strapi-plugin-` という命名パターンを持ち、正規のStrapi CMSプラグインに見せかけていた。`strapi-plugin-cron`、`strapi-plugin-database`、`strapi-plugin-server` など実在しそうな名前を使い、すべてバージョン3.6.8として統一して公開されていた。4つのソックパペットアカウント（`umarbek1233`、`kekylf12`、`tikeqemif26`、`umar_bektembiev1`）が13時間という短期間のうちに一斉にアップロードしており、組織的な攻撃の痕跡が明白だった。SafeDepの動的分析パイプラインが `strapi-plugin-events` を最初に検出し、C2通信シグナルおよび秘密情報の探索行動が確認されたことで調査が始まった。

## 攻撃チェーンの技術的詳細

このサプライチェーン攻撃は `npm install` の実行時に `postinstall.js` スクリプトが自動的に起動することで始まる。SafeDepの分析によれば、8段階（他の調査では11段階）に及ぶ攻撃チェーンが展開される。

まず **Redis RCE**として、`CONFIG SET` コマンドを悪用し、crontabエントリ、PHPウェブシェル（`/app/public/uploads/shell.php`）、SSHキーを注入する。続いてブロックデバイスへのアクセスを試みてraw diskを読み取り、Dockerコンテナ脱出を経てリバースシェル（ポート4444でbash、ポート8888でPython）を展開する。

情報窃取フェーズでは、`.env` ファイルやStrapi設定ファイル、PEM/keyファイルを収集し、Redisの完全ダンプとKubernetesシークレットを抽出する。また、ハードコードされた認証情報（`user_strapi / 1QKtYPp18UsyU2ZwInVM`）でPostgreSQLへの不正接続も試みる。最終的に `/tmp/.node_gc.js` への永続インプラントを書き込み、`144.31.107.231:9999` のC2サーバーと通信を確立する。C2エンドポイントは `/c2/<id>/`（約5分間のC2コマンドポーリング）、`/db/<id>/`（データベース窃取）、`/shell/`（3秒間隔の永続シェルセッション）に分かれており、インプラントが残存している限り攻撃者は継続的なリモートアクセスを維持できる。

## 標的と攻撃者の意図

攻撃者が特定の企業を狙っていたことは、コード内に埋め込まれた手がかりから明らかだ。暗号資産決済プラットフォームであるGuardarianに関連するモジュール名や、`HOT_WALLET`、`COLD_WALLET`、`MNEMONIC` といったウォレット関連の文字列の探索が確認されている。また、永続インプラントの書き込み条件がホスト名「prod-strapi」に限定されていることから、攻撃者がターゲットの本番環境構成を事前に把握していた可能性が高い。Jenkins CI/CDパイプラインへの言及もあり、開発インフラ全体を侵害しようとする意図がうかがえる。

## 見分け方と推奨される対応策

正規のStrapiパッケージは `@strapi/` スコープ付きで公開されているが、悪意あるパッケージはスコープなしで公開することで開発者の信頼を悪用していた。このタイポスクワッティングおよびブランドなりすましの手口は、依存関係を機械的にインストールする開発者にとって見分けにくい。

侵害が疑われる場合、`/tmp/.node_gc.js`、`/tmp/vps_shell.sh`、`/app/public/uploads/shell.php` の存在確認と削除、crontabにおける `node_gc` 参照の除去、IPアドレス `144.31.107.231` への通信遮断を直ちに行う必要がある。また、JWT シークレット、データベース認証情報、APIキーを含む全認証情報のローテーションが推奨される。予防策としては、`npm audit` や Snyk、Dependabot の導入、組織ポリシーによるスコープなしパッケージの拒否設定が有効だ。
