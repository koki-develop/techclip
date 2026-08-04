---
date: "2026-08-04T14:56:13+09:00"
title: "Google Chrome、ARM64版Linux向けにネイティブビルドを静かに提供開始"
description: "GoogleがARM64アーキテクチャのLinux向けにChromeの公式ネイティブビルドを.deb/.rpm形式で提供開始し、Widevine DRMやアカウント同期を含むフル機能が利用可能になった。"
tags:
  - OSS
references:
  - "https://linuxiac.com/google-chrome-quietly-arrives-on-arm64-linux/"
---

## 概要

Googleは、ARM64アーキテクチャのLinux向けにChromeのネイティブビルドを公式ダウンロードページから静かに公開した。Debian・Ubuntu向けの64ビットARM対応.debパッケージと、Fedora・openSUSE向けの.rpmパッケージが用意され、これによりARM64版LinuxユーザーもWidevine DRMやGoogleアカウント同期を含む、他プラットフォーム版と同等のフル機能のChromeを利用できるようになった。

## 背景

これまでARM64アーキテクチャのLinuxユーザーは、公式のGoogle Chromeを利用できず、各ディストリビューションが提供するChromiumビルドやコミュニティ製の代替パッケージに頼らざるを得なかった。GoogleはすでにChrome OS、Apple SiliconのMac、Windows on ARMではARM対応を進めていたが、汎用的なARM64版Linuxへの対応は長らく手つかずのままだった。今回の提供開始は、当初2026年第2四半期（6月末)に予定されていたものが遅延し、8月にずれ込む形で実現した。

## インストール方法と機能

インストールは、公式Chromeダウンロードページから該当ファイルを取得し、ディストリビューションのパッケージマネージャー経由で行う標準的な手順となる。パッケージにはGoogle Chromeの公式リポジトリも同時に追加されるため、以降はAPT・DNF・Zypperを通じた自動アップデートが可能だ。拡張機能やGoogleアカウント同期、各種Googleサービスとの統合など、x86_64版と遜色ない機能セットが備わっている点も特徴で、これまでARM64版Linux環境で制約を受けてきたユーザーにとっては大きな前進となる。

## 今後の展望

ARM64版Linuxは、Raspberry PiやSnapdragon搭載ノートPC、各種サーバー用途などで採用が広がっており、公式Chromeのネイティブ対応はこうしたエコシステムの後押しになると見られる。今回は静かな展開であったため、今後Googleから正式なアナウンスや詳細なロードマップが示されるかが注目される。
