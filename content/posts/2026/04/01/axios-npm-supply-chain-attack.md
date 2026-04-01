---
date: "2026-04-01"
title: "axios npmパッケージがサプライチェーン攻撃に遭う — 北朝鮮帰属のRATが89秒で感染"
description: "週間8,300万ダウンロードのJavaScriptライブラリaxiosのメンテナーアカウントが乗っ取られ、クロスプラットフォームRAT（遠隔操作ツール）を仕込んだバックドア版がnpmに公開された。"
tags:
  - Security
  - OSS
references:
  - "https://www.huntress.com/blog/supply-chain-compromise-axios-npm-package"
  - "https://thehackernews.com/2026/03/axios-supply-chain-attack-pushes-cross.html"
  - "https://www.helpnetsecurity.com/2026/03/31/axios-npm-backdoored-supply-chain-attack/"
---

## 概要

2026年3月31日（UTC）、週間ダウンロード数が約8,300万〜1億に上る人気JavaScriptライブラリ「axios」のnpmパッケージが、サプライチェーン攻撃を受けた。攻撃者はメインメンテナーである Jason Saayman 氏のGitHubおよびnpmアカウントを乗っ取り、ProtonMailアドレスにメールを変更してアカウントから正規オーナーをロックアウト。その後、バックドアを仕込んだバージョン `axios@1.14.1`（`latest`タグ）と `axios@0.30.4`（`legacy`タグ）を立て続けに公開した。悪意あるバージョンが最初に公開されてからわずか89秒でmacOS環境での初感染が検出され、約3時間の露出ウィンドウの間に少なくとも135のエンドポイントが攻撃者のC2インフラと接続したことが確認されている。

攻撃の帰属についてはGoogle Threat Intelligence Groupが北朝鮮国家支援脅威アクター「**UNC1069**（BlueNoroff）」と結論付けた。動機は金銭目的ではなく、スパイ活動・APTと疑われており、仮想通貨採掘やランサムウェアのコンポーネントは含まれていなかった。

## 攻撃の手口と技術的詳細

axiosのソースコード自体は改ざんされておらず、悪意ある依存関係 `plain-crypto-js@4.2.1` が真のドロッパーとして機能した。攻撃者は前日（3月30日 05:57 UTC）に無害な `plain-crypto-js@4.2.0` を公開して事前にスキャン検出を回避するよう偽装し、直前に差し替えるという周到な手法を採った。`npm install axios@1.14.1` を実行するとnpmが依存関係ツリーを解析してこのパッケージを自動インストールし、`postinstall` スクリプト（`setup.js`）がC2サーバーに接続して段階的ペイロードを配信する仕組みになっていた。

RATはmacOS・Windows・Linuxの3プラットフォームに対応したペイロードを持ち、それぞれ以下の方法で動作した。

- **macOS**：AppleScriptが `sfrclak.com:8000` からバイナリを取得し `/Library/Caches/com.apple.act.mond` に保存・実行
- **Windows**：PowerShellが `%PROGRAMDATA%\wt.exe` にバイナリをコピーし、VBScriptでペイロードを取得。レジストリのRunキーで永続化
- **Linux**：Pythonスクリプトを `/tmp/ld.py` に取得し `nohup` で実行

RATの主な機能はシステム偵察・フィンガープリンティング、60秒ごとのC2へのビーコン送信、任意コマンド実行、ファイルシステム列挙、インメモリバイナリインジェクション（Windows）など。さらに実行後は `package.json` をクリーンな状態に置き換えてフォレンジック検出を回避し、この全工程が約15秒で完了するという高い完成度を示した。

## 影響範囲と緊急対応

悪意あるバージョンの稼働時間は `1.14.1` で約2時間53分、`0.30.4` で約2時間15分にとどまったが、axiosがクラウドおよびコード環境の約80%に存在するという普及率から、その影響は広範に及んだ可能性がある。影響を受けた環境の約3%でRAT実行が確認されている。

影響を受けた可能性のあるシステムに対しては、以下の緊急対応が推奨されている。

1. `axios@1.14.0` または `axios@0.30.3` へのダウングレード
2. `plain-crypto-js` を `node_modules` から削除し、`package.json` に `overrides` ブロックを追加
3. CI/CDパイプラインのログを確認し、`sfrclak[.]com` や `142.11.206.73` へのアウトバウンドトラフィックをブロック
4. RATアーティファクト（macOS: `/Library/Caches/com.apple.act.mond`、Windows: `%PROGRAMDATA%\wt.exe`）が発見された場合はシステムを既知の状態から再構築（その場でのクリーンアップは非推奨）
5. npmトークン、AWS/GCP/Azure認証情報、SSH秘密鍵、CI/CDシークレット、`.env` ファイルの値などすべての認証情報をローテーション
6. CI/CDパイプラインでは `--ignore-scripts` フラグを用いて `postinstall` フックの実行を防止

また、npm エコシステム全体のセキュリティとして、GitHub Actions OIDC Trusted Publishing を設定済みでも長期有効な `NPM_TOKEN` が残存していたことが今回の侵害を可能にしたと分析されている。Trusted Publishing への完全移行と古いトークンの削除が強く推奨される。

## 背景と今後の懸念

本件は、TeamPCP（財政的動機を持つ別グループ）による Aqua Trivy・CheckMarx VS Code拡張・LiteLLM・Telnyx などへのサプライチェーン攻撃の数日後に発生しており、npmエコシステムを標的とした攻撃の連続性を示している。Mandiant の CTO は、今回のような攻撃で盗まれた認証情報が「数日〜数ヶ月にわたるさらなるサプライチェーン攻撃、SaaS環境侵害、ランサムウェア、暗号資産窃盗」に連鎖するリスクがあると警告しており、侵害を受けた組織は単なる復旧にとどまらず、包括的なフォレンジック調査を実施することが求められる。
