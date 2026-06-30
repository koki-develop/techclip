---
date: "2026-07-01T02:40:55+09:00"
title: "乗っ取られたnpm・GoパッケージがVS Code自動実行とブロックチェーンデッドドロップを悪用、5段階サプライチェーン攻撃を展開"
description: "JFrogが発見したサプライチェーン攻撃では、ハイジャックされたnpmおよびGoパッケージがVS CodeのfolderOpenトリガーとブロックチェーンのデッドドロップを組み合わせ、5段階の攻撃チェーンでブラウザ認証情報や暗号資産ウォレット情報を窃取するPython製マルウェアを展開する。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/hijacked-npm-and-go-packages-use-vs.html"
  - "https://research.jfrog.com/post/hijacked-npm-vscode-tasks-blockchain/"
---

## 概要

JFrog Securityの研究者は、2026年5月25日にnpmレジストリへアップロードされた2つの悪意あるパッケージ（`html-to-gutenberg` v4.2.11、`fetch-page-assets` v1.2.9）を起点とするサプライチェーン攻撃を発見した。その後、同一のペイロードを含む16個のGitHub上のGoパッケージも特定されている。この攻撃はVS Codeのタスク自動実行機能とブロックチェーンのデッドドロップという2つの新手な技術を組み合わせており、北朝鮮と関連するとされる「Fake Font」グループ（Contagious Interviewキャンペーンの一部）に帰属されている。

## VS Codeタスクを悪用した新手の実行手法

この攻撃の最大の特徴は、npm v12で強化されたライフサイクルスクリプト制限を回避するため、`.vscode/tasks.json`を利用している点だ。`runOptions.runOn: 'folderOpen'`という設定を持つ「eslint-check」という無害に見えるタスクが仕込まれており、開発者がプロジェクトフォルダをVS Codeのワークスペースとして開いた瞬間にマルウェアが自動実行される。悪意あるペイロードは`public/fonts/fa-solid-400.woff2`というフォントファイルに偽装したJavaScriptコードとして隠蔽されており、不審なエントリポイントを気づきにくくしている。

## ブロックチェーンによる耐久性の高いC2インフラ

第1ステージの偽フォントローダーが実行されると、TronGridやAptos、BSCのJSON-RPCエンドポイントといった正規のパブリックブロックチェーンサービスのトランザクションデータから暗号化されたペイロードを取得する。`?.?`区切り文字で囲まれたデータをXORデコードする仕組みであり、これらのブロックチェーンインフラを「デッドドロップ」として活用することで、従来の手法ではC2サーバーのドメインやIPをブロックされても攻撃を継続できる耐久性を実現している。

## 5段階攻撃チェーンと窃取対象

攻撃は5段階で構成される。(1) 偽フォントローダーによるブロックチェーンからのペイロード取得、(2) 被害者識別マーカー（`Sec-V`ヘッダー）に基づくC2サーバーへの接続、(3) シェル実行・クリップボードアクセス・任意JavaScript実行（`ss_eval`コマンド）が可能なSocket.ioバックドアの常駐化、(4) Pythonインタープリタのダウンロードを含むPythonローダーの展開、(5) 包括的な情報窃取マルウェアの実行、という流れだ。

窃取対象は非常に幅広く、Chromium系およびFirefoxブラウザの認証情報、1Password・LastPass・Bitwardenなどのパスワードマネージャー、MetaMask・Phantom・Trust Walletを含む30種類以上の暗号資産ウォレット、Gitや GitHub Desktop・VS Codeのストレージ、Windows Credential Manager・macOS Keychain・Linux Secret ServiceといったOS認証情報ストア、さらにDropbox・OneDrive・Google Driveなどのクラウドストレージメタデータが含まれる。収集したデータはZIPアーカイブに圧縮され、C2サーバーまたはTelegramボットに送信される。また、クラウド環境・CIランナー・サンドボックスを検出すると完全な動作を無効化するアンチ検出機能も備えている。

## 検出と対策

JFrog XrayはXRAY-1008590およびXRAY-1008535として両パッケージを検出する。侵害を受けた可能性のある開発者は、該当パッケージのアンインストール、`.vscode/tasks.json`の不審なfolderOpenトリガーの確認、`~/.node_modules`や`%USERPROFILE%\.npm`などのアーティファクト削除に加え、npmトークン・GitHubアクセスキー・SSHキー・クラウド認証情報・ブラウザパスワード・ウォレット秘密鍵などすべての認証情報をローテーションする必要がある。C2インフラのIPアドレス（`166.88.134.62`、`198.105.127.210`、`23.27.202.27`）はネットワーク境界でブロックすることが推奨される。
