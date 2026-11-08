---
date: "2026-11-09T08:07:02+09:00"
title: "Rails 8.0.5.2/8.1.4.1公開、Active StorageのImageMagick処理に起因する重大な任意ファイル読み書き脆弱性など21件を修正"
description: "Ruby on RailsコアチームがセキュリティリリースRails 8.0.5.2と8.1.4.1を公開し、Active StorageのImageMagick処理における任意ファイル読み書き・リモートコード実行の脆弱性を含む21件のセキュリティ問題を修正した。"
tags:
  - Programming Languages
  - Security
references:
  - "https://discuss.rubyonrails.org/t/rails-security-releases-8-0-5-2-and-8-1-4-1/91802"
---

## 概要

Ruby on Railsコアチームは11月4日、セキュリティリリース「8.0.5.2」と「8.1.4.1」を公開した。今回のリリースでは合計21件のセキュリティ問題が修正されており、中でもActive StorageがImageMagickを用いて画像・動画を処理する際に発生する任意ファイル読み書きの脆弱性がCritical相当として扱われている。影響を受けるアプリケーションを運用している開発者には、速やかなアップグレードが強く推奨されている。

## Active Storageの深刻な脆弱性

今回最も重要度が高いとされるのが、Active Storageの画像・動画処理に関する一連の脆弱性だ。GHSA-f3w6-w445-fwh9は画像分析処理において任意のファイルを読み書きできてしまう問題でCriticalに分類されており、GHSA-v924-7rp8-4mxhはビデオのプレビュー生成・分析・画像処理の過程で任意ファイルの読み取りに加えリモートコード実行(RCE)につながる可能性があるとして深刻度Highとされている。さらにGHSA-3f4q-8x5m-76v8は、ビデオのプレビュー・分析時にローカルファイルが開示されうる問題で、こちらはLowに分類されている。いずれもActive StorageがImageMagickなどの外部処理系を呼び出す経路に起因しており、ユーザーがアップロードしたファイルを処理する機能を持つRailsアプリケーションは影響を受ける可能性がある。

## その他の修正内容

今回のリリースではActive Storage関連以外にも幅広い問題が修正されている。Strong ParametersのバイパスやIPスプーフィング(8.1系のみ)はHighに分類される認証・パラメータ処理関連の脆弱性だ。またテキストヘルパー、highlightヘルパー、strip_tags、タグヘルパー、さらに8.1系ではMessagePackシリアライザーに関するXSS脆弱性も複数Mediumとして報告されている。サービス拒否(DoS)に関連する問題としては、Active Supportのsafe_constantizeがHigh、Action Controller LiveストリーミングとActive Storageのファイル名処理がMediumとされた。その他にも、キャッシュストアを利用したセッション復元、Google Cloud Storageへの直接アップロード時における署名なしContent-Typeやサイズ制限回避、キャッシュポイズニング、Mailgunの署名リプレイ、SameSite属性の欠落など、幅広い種類の問題が合わせて修正されている。

## アップグレードの推奨と今後

Railsコアチームは、影響を受けるすべてのアプリケーションに対し、できるだけ速やかなアップグレードを強く勧告している。なお8.0系のサポート終了は2026年11月7日とされており、まだアップグレードしていない運用者は少なくとも8.0系の最新パッチへの更新が推奨される。各脆弱性にはGitHub Security Advisory(GHSA)のリンクと詳細なパッチが公開されており、即時にアップグレードできない場合の緩和策の検討にも利用できる。ダウンロードしたgemファイルの検証用にSHA-256ハッシュも併せて公開されており、サプライチェーンの観点からの確認も可能となっている。
