---
date: "2026-04-04T18:11:41+09:00"
title: "Progress ShareFileの認証前RCEチェーン（CVE-2026-2699・CVE-2026-2701）が公開、約3万台に影響"
description: "Progress ShareFileのStorage Zones Controllerに認証バイパスとRCEを組み合わせた脆弱性チェーンが発見され、未認証の攻撃者がWebシェルを設置可能なことが明らかになった。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/new-progress-sharefile-flaws-can-be-chained-in-pre-auth-rce-attacks/"
  - "https://labs.watchtowr.com/youre-not-supposed-to-sharefile-with-everyone-progress-sharefile-pre-auth-rce-chain-cve-2026-2699-cve-2026-2701/"
  - "https://www.cybersecuritydive.com/news/researchers-critical-flaws-progress-sharefile/816599/"
---

## 概要

セキュリティ研究機関のwatchTowrは2026年4月2日、Progress ShareFileのStorage Zones Controller（SZC）に存在する2つの脆弱性を組み合わせた認証前リモートコード実行（Pre-Auth RCE）チェーンを公開した。CVE-2026-2699（認証バイパス）とCVE-2026-2701（RCE）を連鎖させることで、未認証の攻撃者が対象サーバーにASPX Webシェルを設置できる。影響を受けるのはSZCのASP.NETブランチ5.x系（バージョン5.12.3以前）で、インターネットに公開されているインスタンスは約3万台に上るとされている。

## 脆弱性の技術的詳細

CVE-2026-2699は「Execution After Redirect（CWE-698）」に分類される認証バイパス脆弱性だ。`/ConfigService/Admin.aspx`のコードが`Response.Redirect(path, false)`を第2引数に`false`を指定して呼び出しているため、HTTPリダイレクト（302レスポンス）を返した後もページ処理が継続して実行される。攻撃者はHTTPリダイレクト（302レスポンス）を無視してレスポンスボディを直接読み取るだけで管理パネルへの認証をバイパスできる。

CVE-2026-2701のRCEは次の3ステップで実現される。まず「Network Share Location」フィールドをWebルートディレクトリ（例：`C:\inetpub\wwwroot\ShareFile\StorageCenter\documentum`）に変更する。次にゾーン設定変更時にアプリケーションが自動補完するパスフレーズから暗号化キーを入手する。最後に`/upload.aspx`エンドポイントへ`unzip=true`パラメータ付きでASPX Webシェルを含むZIPファイルをアップロードすると、展開処理がファイル拡張子を保持したままWebルート配下に展開し、Webシェルが設置される。なお、`TempData2`パラメータに含まれるBase64エンコード・AES暗号化されたZone Secretは、固定ソルト値`p3510060xfZ2s9`とパスフレーズを用いて復号され、復号されたZone Secretがアップロードリクエストの署名に使用されるHMAC-SHA256の鍵として用いられる。

## 影響範囲と対応状況

FOFAの調査によると、インターネットに公開されているSZCインスタンスは約3万台。ShadowServer Foundationは700件のエクスポーズされたインスタンスを確認しており、米国・欧州への集中が見られる。公開時点（2026年4月2日）では実際の悪用は観測されていない。

Progressはすでに2026年3月10日にバージョン5.12.4で修正を提供している。今回の公開開示により脅威アクターを引き付ける可能性があるため、影響を受けるバージョンを運用中の組織は速やかにアップデートを適用することが推奨される。

## 背景と歴史的文脈

Progress ShareFileをめぐっては、2023年にも認証バイパス脆弱性（CVE-2023-24489）が悪用されてランサムウェア攻撃に利用された前例がある。今回の脆弱性チェーンはAccellion、SolarWinds Serv-U、MOVEitといったファイル転送・共有ソリューションを標的とした一連の攻撃パターンとも重なる。Clopをはじめとするランサムウェアグループがこうした製品の脆弱性を積極的に悪用してきた歴史から、早期パッチ適用の重要性が改めて強調されている。
