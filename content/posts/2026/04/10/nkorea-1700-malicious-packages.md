---
date: "2026-04-10T10:39:13+09:00"
title: "北朝鮮「Contagious Interview」、npm・PyPI・Go・Rustなど5エコシステムに1,700超の悪意あるパッケージを配布"
description: "北朝鮮関連の攻撃グループ「Contagious Interview」が、複数のオープンソースパッケージエコシステムを悪用して開発者を標的にした大規模サプライチェーン攻撃を展開していることが判明した。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/04/n-korean-hackers-spread-1700-malicious.html"
---

## 概要

北朝鮮に関連する攻撃グループ「Contagious Interview」が、npm・PyPI・Go・Rust・Packagistの5つのオープンソースパッケージエコシステムを横断して、1,700件以上の悪意あるパッケージを配布していたことが明らかになった。Socket社のリサーチャーが2025年1月以降のキャンペーンを追跡・調査した結果として報告されており、開発者ツールに偽装したパッケージを通じて開発者環境への侵入を図るサプライチェーン攻撃の大規模な実態が浮かび上がった。

## 影響を受けるパッケージと技術的詳細

攻撃はエコシステムをまたいで実施されており、確認されたパッケージは以下の通りである。npmでは `dev-log-core`・`logger-base`・`logkitx`・`pino-debugger`・`debug-fmt`・`debug-glitz` の6パッケージ、PyPIでは `logutilkit`・`apachelicense`・`fluxhttp`・`license-utils-kit` の4パッケージ、Goでは `github.com/golangorg/formstash` と `github.com/aokisasakidev/mit-license-pkg` の2パッケージ、Rustでは `logtrace`、Packagistでは `golangorg/logkit` がそれぞれ確認されている。

悪意あるコードはインストール時ではなく、一見正当に見える関数の呼び出し時に実行される点が特徴的だ。たとえばRustパッケージでは `Logger::trace(i32)` というメソッド内にマルウェアが埋め込まれており、セキュリティ検査をすり抜けやすい設計となっている。ペイロードはWebブラウザ・パスワードマネージャ・暗号資産ウォレットからのデータ窃取を行うほか、Windows環境ではリモートシェルコマンド実行・キーロギング・ファイルアップロード・AnyDeskを用いたリモートアクセスといった包括的な侵害後機能を備えた完全なインプラントとして機能する。

## 関連する攻撃活動と背景

本キャンペーンと並行して、UNC1069と呼ばれるグループによるAxiosのnpmパッケージへの汚染も確認されている。Telegram・LinkedIn・Slackを通じた数週間にわたるソーシャルエンジニアリングキャンペーンの後、悪意あるミーティングリンクを通じてWAVESHAPER.V2マルウェアを配布する手口が用いられており、標的となる開発者への接触が組織的かつ段階的に行われていることが窺える。

一連の活動は北朝鮮による外貨獲得および情報収集を目的とした国家レベルの攻撃インフラとして機能しており、オープンソースエコシステムへの信頼を悪用した開発者向けサプライチェーン攻撃が継続的に拡大していることを示している。開発者は使用するパッケージの出所を慎重に確認し、特にロギングやユーティリティ系の軽量パッケージへの依存には注意が必要だ。