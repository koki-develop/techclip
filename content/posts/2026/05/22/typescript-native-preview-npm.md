---
date: "2026-05-22T02:43:51+09:00"
title: "Go製TypeScriptネイティブコンパイラがnpmで公開、Sentryで72秒→6秒の劇的速度向上"
description: "MicrosoftがGo言語で書き直したTypeScriptネイティブコンパイラをnpmパッケージ「@typescript/native-preview」として公開し、大規模コードベースで従来比約10倍の処理速度向上を実現したと発表した。"
tags:
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/typescript/announcing-typescript-native-previews/"
  - "https://www.infoworld.com/article/3996134/microsoft-rolls-out-typescript-native-previews.html"
  - "https://socket.dev/blog/typescript-native-previews-now-on-npm-for-public-testing"
---

## 概要

MicrosoftはTypeScriptコンパイラをJavaScriptからGo言語に書き直したネイティブバージョン「TypeScript Native Previews」を発表し、npmパッケージ「`@typescript/native-preview`」として公開した。プロジェクト内部では「Corsa」と呼ばれるこのコンパイラは、従来のJavaScript製コンパイラ（社内コードネーム「Strada」）と比べて大多数のプロジェクトで約10倍の処理速度向上を実現している。VS Code向けの拡張機能「TypeScript (Native Preview)」もマーケットプレイスで提供されており、誰でも試せる状態になった。

## インストールと利用方法

開発者は以下のコマンドでプレビュー版をインストールして試すことができる。

```bash
npm install -D @typescript/native-preview
npx tsgo --project ./src/tsconfig.json
```

新しい実行ファイル`tsgo`は従来の`tsc`と同様の使い勝手で動作する。VS Codeユーザーはマーケットプレイスから拡張機能をインストールし、「TypeScript Native Preview: Enable (Experimental)」コマンドで有効化することで、ネイティブコンパイラを使ったエディタ体験を試せる。

## 劇的な速度向上の実績

Go言語への移植によって得られた最大の恩恵は処理速度の大幅な向上だ。Goはネイティブコンパイルと共有メモリによる並行処理をサポートしており、これはJavaScriptが本質的に持っていない特性だ。実際のコードベースを使ったベンチマークでは、大規模OSSプロジェクトSentryのコードベースにおいてTypeScript 5.8での72.81秒という処理時間が、ネイティブバージョンでは6.761秒にまで短縮されたことが確認されている。

## 現時点の機能と制限

3月の初回発表以降、今回のプレビューでは新たにJSXの型チェックサポート、JSDocアノテーション付きJavaScriptファイルの型チェック対応、コード補完機能が追加された。一方で、現時点では`--declaration`（型定義ファイルの生成）、`--build`モード、ES5などのダウンレベルコンパイルターゲットはまだサポートされていない。エディタ機能においても、自動インポート、全参照検索、リネームといった高度な機能は引き続き開発中だ。

## 今後のロードマップ

Microsoftは年内に`--build`モードや拡充されたランゲージサービス機能を備えた、より完全なコンパイラバージョンのリリースを目指している。TypeScript 7.0では最終的に`tsgo`が`tsc`に改名され、公式の`typescript` npmパッケージに統合される計画だ。一方、TypeScript 6.xシリーズでは既存のJavaScript製コンパイラ「Strada」が引き続きサポートされ、段階的な移行が可能な体制が整えられる。
