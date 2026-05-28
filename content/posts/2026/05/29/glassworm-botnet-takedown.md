---
date: "2026-05-29T03:05:20+09:00"
title: "CrowdStrikeとGoogleがGlasswormボットネットを摘発、SolanaとBitTorrentを悪用した耐障害性C2インフラを同時無力化"
description: "CrowdStrike、Google、Shadowserver Foundationが共同作戦により、SolanaブロックチェーンやBitTorrent DHTなど4チャネルで構成されたGlasswormボットネットのC2インフラを2026年5月27日に同時停止させた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/glassworm-botnet-disrupted-after-resilient-c2-infrastructure-takedown/"
  - "https://www.theregister.com/cyber-crime/2026/05/27/crowdstrike-google-shatter-glassworm-botnet/5247337"
  - "https://techcrunch.com/2026/05/27/crowdstrike-and-google-take-down-botnet-used-by-hackers-to-target-software-developers-in-supply-chain-attacks/"
---

## 概要

CrowdStrikeのCounter Adversary Operations、Google Threat Intelligence Group、そして非営利組織のShadowserver Foundationは2026年5月27日14:00 UTC、「Glassworm」と名付けられたボットネットのテイクダウン作戦を実施した。Glasswormは2025年初頭から活動を開始し、オープンソースソフトウェア開発者を狙ったサプライチェーン攻撃に使われてきた。300以上のGitHubリポジトリに悪意あるコードを注入し、400以上のソフトウェア成果物に影響を与えるなど、開発者コミュニティに深刻な被害をもたらした。

## 巧妙な4チャネルC2インフラ

Glasswormの最大の特徴は、単一障害点を排除するために設計された4つの独立したコマンド＆コントロール（C2）チャネルだ。

1. **Solanaブロックチェーン** — ブロックチェーントランザクションのメモフィールドにC2サーバーアドレスを埋め込み、改ざんが困難な分散台帳を通信経路として活用した。
2. **BitTorrent DHT（分散ハッシュテーブル）** — ハードコードされた公開鍵を使用してP2Pネットワーク経由で設定データを取得。中央サーバーを持たないため従来の手法では遮断できない。
3. **Google Calendar** — イベントタイトルにBase64エンコードされたC2パスを隠蔽し、正規サービスの通信に紛れ込ませた。
4. **従来型VPSサーバー** — ペイロード配信用の直接接続チャネルとして使用。

攻撃者は個々のチャネルが遮断されても残りを通じて運用を継続できる設計を採用していた。そのため今回のテイクダウンには「すべてのチャネルを同時に遮断する精度とタイミング」が不可欠であったと、セキュリティチームは説明している。摘発後、感染した端末はCrowdStrikeが管理するIPアドレス `164.92.88[.]210` へのビーコンを送るようになり、感染システムの特定が可能となった。

## 攻撃手法と被害の詳細

Glasswormは当初、OpenVSX上のVS Code拡張機能を標的としていたが、その後npmパッケージやPythonパッケージ、GitHubリポジトリへと攻撃範囲を拡大した。攻撃者は複数の手法を組み合わせて開発者アカウントを侵害した。過去に流出した認証情報を使った不正ログイン、悪意ある拡張機能のマーケットプレイスへの公開、そして検索結果のスポンサー枠を悪用したマルバーティジング（不正広告）による誘導がその主な手口だ。

感染後は不可視Unicodeを用いたコード注入をWindows・macOS・Linux全プラットフォームで実行し、暗号資産ウォレットや開発者の認証情報を窃取した。さらに「GlasswormRAT」と呼ばれるNode.js製のリモートアクセスツールを展開し、感染環境内での横展開（ラテラルムーブメント）を可能にした。

## 検出と今後の対応

セキュリティ研究チームは感染したシステムを特定するためのYARAルールを公開している。組織は `164.92.88[.]210` へのネットワーク接続履歴を調査することで感染の有無を確認できる。今回の摘発はGlasswormの活動を大きく制約するものだが、ブロックチェーンやP2Pネットワークを悪用した耐障害性の高いC2インフラの台頭は、今後のサイバーセキュリティにおける新たな課題を浮き彫りにした。開発者が利用するサプライチェーンの各経路—パッケージリポジトリ、IDE拡張機能、コードホスティングサービス—が攻撃対象になり得ることを改めて示した事例として、業界全体への警鐘となっている。
