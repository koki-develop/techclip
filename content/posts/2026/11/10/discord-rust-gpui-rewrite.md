---
date: "2026-11-10T08:06:59+09:00"
title: "DiscordがElectronを捨ててRust化、新クライアントのメモリ使用量は290MBに"
description: "DiscordがデスクトップおよびモバイルクライアントをElectron/React NativeからRustとGPUIフレームワークへ移行し、メモリ使用量を4GBから290MBへ大幅に削減すると発表した。"
tags:
  - Programming Languages
references:
  - "https://www.heise.de/en/news/Discord-is-rebuilding-in-Rust-leaving-React-and-Electron-behind-11516113.html"
  - "https://www.windowslatest.com/2026/11/05/discord-is-killing-its-electron-app-that-can-eat-4gb-of-ram-on-windows-11-and-the-rust-rebuild-uses-just-290mb/"
  - "https://www.ghacks.net/2026/11/06/discord-is-rebuilding-its-desktop-app-in-rust-with-the-new-client-using-290-mb-of-ram/"
---

## 概要

Discordはデスクトップおよびモバイルクライアントを、ElectronおよびReact NativeからRustとGPUIフレームワークへ全面的に移行することを明らかにした。CTOのStanislav Vishnevskiy氏がX（旧Twitter）上で発表したもので、早期ビルド「Discord Phoenix」ではメモリ使用量が約290MBに抑えられているという。現行のElectron版はアイドル時でも1〜2GB、通常利用時には最大4GBのRAMを消費することがあり、WindowsではDiscordがメモリ使用量4GB超過時に自動再起動する機能を導入していたほど資源消費の大きさが問題視されていた。正式なリリース時期は未定だが、両者を比べれば10倍以上のメモリ削減となる見込みだ。

## 技術的な詳細

新クライアントはデスクトップ向けにRustコアとGPUIによる描画を採用する。GPUIはGPUアクセラレーションを利用するUIフレームワークで、macOSではMetal、WindowsではDirectX 11、Linuxではwgpuをバックエンドとしてレンダリングを行う。Zed Industries製のエディタ「Zed」で使われているフレームワークであり、Discordはこれを採用する主要な外部企業となる。ただしGPUI自体はまだバージョン1.0に達しておらず、今後の開発においてAPIの互換性問題などが課題になる可能性がある。モバイル版はAndroid・iOSともにネイティブUIを維持しつつ、アプリケーションロジックをRustで共有することで、プラットフォーム間の実装の重複を解消する狙いがある。なお、YouTubeやActivitiesなどのWeb埋め込みコンテンツは引き続きシステムのWebViewを利用する。Electron版で起動時に表示される「Starting」画面もなくなり、Chromiumエンジンの初期化が不要になることで起動時間の改善も期待されている。

## 背景と今後の展望

DiscordはRustを2018年から段階的に採用してきた企業であり、インフラや音声処理技術、そして現行クライアントの一部にも既にRustが使われている。2020年にはメッセージ読み込みサービスをGoからRustへ移行し、ガーベジコレクションに起因するレイテンシ問題を解消した実績もある。Vishnevskiy氏は「クライアント全体をRust化することが聖杯（holy grail）だった」と述べており、今回の取り組みはその集大成と位置づけられる。Electronは各アプリが個別にChromiumを同梱するため、PC上で起動しているアプリの数だけリソースの重複が発生する構造的な問題を抱えており、Discordはその代表例として長年指摘されてきた。今回示された早期ベンチマークは好材料だが、実際のユーザー環境でどの程度の効果が出るかは、Discord Phoenixが広く提供された後の実地検証が必要になる。
