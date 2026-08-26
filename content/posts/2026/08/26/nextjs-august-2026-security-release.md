---
date: "2026-08-26T20:07:10+09:00"
title: "Next.jsが緊急セキュリティリリース、AVIF画像経由の未認証RCEとWindows環境のRCEを修正"
description: "Next.jsチームがバージョン16.3.3および15.5.24を公開し、AVIF画像最適化を悪用した未認証リモートコード実行とWindows環境でのRCEという2件の重大な脆弱性を修正した。"
tags:
  - Programming Languages
  - Security
references:
  - "https://nextjs.org/blog/august-2026-security-release"
  - "https://vercel.com/changelog/nextjs-august-2026-security-release"
---

## 概要

Next.jsチームは8月25日、Active LTS系列のv16.3.3とMaintenance LTS系列のv15.5.24をリリースし、深刻度「Critical」の脆弱性を2件修正した。1件目は画像最適化APIがAVIF画像を処理する際に、内部で利用する`sharp`ライブラリの依存先である`libheif`の脆弱性（GHSA-g89c-p67h-r497）を突かれることで、未認証のリモートコード実行が可能になるというもの（Next.js側の識別子はGHSA-2xp9-vwfh-vxw4）。2件目はPages RouterとApp Routerを併用し、かつCache Componentsを使用していないアプリケーションをWindows上のファイルシステムでホストしている場合に、未認証のRCEが成立するというもの（CVE-2026-75604 / GHSA-p293-qw3h-jr36）。後者はLinuxおよびmacOS環境では発生せず、既知の回避策も存在しないため、該当するWindows環境のユーザーは早急なアップデートが求められる。

Next.jsチームは5日前の8月20日に今回のリリース予告を行っていたが、公開当日に追加のCritical脆弱性を新たに特定したことを受けてリリース時期を前倒ししたと説明している。

## 技術的な詳細

AVIF関連の脆弱性は、Next.jsの画像最適化APIが攻撃者の制御下にあるAVIF画像を処理する過程で、依存ライブラリ`sharp`が利用する`libheif`のデコード処理に起因する欠陥を突かれることで発生する。上流のlibheif側での修正が完全に行き渡るまでの措置として、パッチ適用版のNext.jsではAVIF画像の最適化処理自体を無効化する対応が取られている。つまり、AVIF画像はそのままの形で配信され、脆弱性のある処理経路を通過しなくなる。

Windows関連の脆弱性は、Pages RouterとApp Routerの両方を組み合わせて使用し、かつCache Componentsを有効化していない構成のアプリケーションが対象となる。Next.jsサーバーがWindowsのファイルシステム上で動作している場合にRCEへとつながる可能性があり、Linux・macOS環境は影響を受けない。回避策が存在しないため、該当環境の運用者はアップデート以外に有効な対処手段がない。

修正版へのアップデートは以下のコマンドで行える。

```bash
npm install next@15.5.24  # 15.5系の場合
npm install next@16.3.3   # 16.3系の場合
```

## Vercelでのホスティングへの影響

Vercelは自社プラットフォーム上にホストされているNext.jsアプリケーションについて、両脆弱性から既に保護されていると発表した。同社によれば、ユーザー側でのアップグレードや設定変更、再デプロイは一切不要だという。AVIF関連の脆弱性については、Vercelの画像最適化サービス全体でAVIF最適化処理をあらかじめ無効化しており、悪意のあるAVIFファイルが送られてきても脆弱な処理経路を通らずそのまま配信される。Windows関連の脆弱性についても、Vercelのランタイムは元々Linux上で稼働しているため影響を受けない。一方で自前でホスティングしている運用者は、この保護の恩恵を受けられないため、速やかにNext.js 15.5.24または16.3.3へのアップグレードが必要となる。

Next.jsチームは、こうした脆弱性の発見と対応がVercelのオープンソースバグバウンティプログラムを通じた研究者との協力によるものだとしており、セキュリティ体制の強化を継続する姿勢を示している。
