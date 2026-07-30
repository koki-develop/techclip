---
date: "2026-07-31T02:34:30+09:00"
title: "Rails Active Storageに任意ファイル読み取り・RCEの脆弱性、libvips連携の未対策が原因"
description: "Ruby on RailsチームがActive Storageのlibvips画像処理に起因する任意ファイル読み取り・リモートコード実行の脆弱性(CVE-2026-66066)を修正し、7.2.3.2/8.0.5.1/8.1.3.1をリリースした。"
tags:
  - Programming Languages
  - Security
references:
  - "https://rubyonrails.org/2026/7/29/Rails-Versions-7-2-3-2-8-0-5-1-and-8-1-3-1-have-been-released"
  - "https://discuss.rubyonrails.org/t/cve-2026-66066-possible-arbitrary-file-read-and-remote-code-execution-in-active-storage-variant-processing/91432"
---

## 概要

Ruby on Railsチームは2026年7月29日、Active Storageの画像バリアント処理に起因する任意ファイル読み取りおよびリモートコード実行(RCE)の脆弱性(CVE-2026-66066)を修正するセキュリティリリースとして、Rails 7.2.3.2、8.0.5.1、8.1.3.1を公開した。この脆弱性はEthiack社のセキュリティ研究者らによって「KindaRails2Shell」と名付けられ、Critical(緊急)なRCEとして報告されている。Railsチームは全ユーザーに対し可能な限り速やかなアップグレードを強く推奨している。

## 技術的な詳細

Active Storageの画像処理バックエンドとして利用されるlibvipsは、"loaders"と"savers"と呼ばれるファイル形式の処理機能を持つが、その一部は信頼できない入力に対して安全性が検証されていない「unfuzzed」な操作としてマークされている。Active Storageはこれらの危険な操作を無効化しないままlibvipsを利用していたため、攻撃者が細工したファイルをアップロードし画像バリアントを生成させることで、任意ファイルの読み取りやリモートコード実行につなげられる状態にあった。この問題は、libvipsを使用し(デフォルト設定)、信頼できないユーザーからのファイルアップロードを許可しているアプリケーションが影響を受ける。バリアントの生成自体が不要な場合でも影響が及ぶ点が注意点として挙げられている。

影響を受けるのは、activestorage 7.2.3.2未満、8.0系で8.0.5.1未満、8.1系で8.1.3.1未満のバージョンだ。修正にはRails本体のアップデートに加え、libvips 8.13以上へのアップグレードが必須となる。libvipsが8.13未満の場合、unfuzzed操作を無効化できずRails起動時に例外が発生する仕様になっている。即座にlibvipsをアップグレードできない環境向けには、libvips 8.13以上であれば環境変数`VIPS_BLOCK_UNTRUSTED`を設定する、あるいはruby-vips 2.2.1以上であれば初期化コードで`Vips.block_untrusted(true)`を呼び出すという回避策も示されている。

## 対応の緊急性

この脆弱性は任意ファイル読み取りを許すため、`secret_key_base`をはじめとする環境変数上のシークレットが露出するおそれがある。Railsチームは、パッチ適用と併せて、secret_key_base、マスターキーおよび暗号化認証情報、ストレージサービスの認証情報、データベース認証情報、外部サービスのトークンなど、環境変数に含まれる全てのシークレットをローテーションするよう強く推奨している。なお、脆弱性の技術的な詳細については、悪用の拡大を防ぐため2026年8月28日までに公開される予定だ。この脆弱性はEthiack社の0xacb、s3np41k1r1t0、castilho、およびGMO Flatt Security IncのRyotaKによって責任ある形で報告された。

古いバージョンのRailsはサポート対象外であり、Railsチームは少なくとも7.2系以上へのアップグレードを推奨している。Active Storageで信頼できないユーザーからのファイルアップロードを扱っているアプリケーションの運用者は、バージョン更新とlibvipsのアップグレード、シークレットのローテーションを速やかに実施する必要がある。
