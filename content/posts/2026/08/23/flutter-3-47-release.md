---
date: "2026-08-23T20:03:54+09:00"
title: "Flutter 3.47リリース、MaterialとCupertinoを独立パッケージ化しWebAssembly標準化へ前進"
description: "Googleが発表したFlutter 3.47では、MaterialとCupertinoのUIライブラリが本体から分離され、Web出力のWebAssembly標準化に向けた方針が示された。"
tags:
  - Programming Languages
references:
  - "https://www.publickey1.jp/blog/26/fluter_347uiwebassembly.html"
---

## 概要

Googleは2026年8月12日、クロスプラットフォーム開発フレームワークFlutterの最新版「Flutter 3.47」を正式リリースした。今回の目玉は、これまでFlutter本体に統合されていた「Material」と「Cupertino」の2つのUIライブラリがスタンドアロンパッケージとして分離されたことだ。MaterialはGoogleの「Material Design」に準拠し、Android・Windows・Webアプリ向けのUI構築に適したライブラリ、CupertinoはAppleの「Human Interface Guidelines」に準拠し、iOS向けUI構築に特化したライブラリである。これらがFlutter本体から独立したことで、それぞれ独自のリリースサイクルで更新できるようになった。

## 技術的な詳細

UIライブラリの分離による最大の利点は、プラットフォーム側の仕様変更に対して迅速に追随できる点にある。たとえばAppleがiOSのデザインガイドラインを更新した際、これまではFlutar本体のアップデートを待つ必要があったが、今後はCupertinoパッケージ単体で即座に対応できる。また、開発者が独自のデザインシステムを構築しやすくなる効果も見込まれている。

Web出力に関しては、現在HTML・CSS・JavaScriptで生成されているコンテンツに加え、将来的にはデフォルトでWebAssemblyも自動生成する方向性が示された。WebAssembly出力自体はビルドオプションとして既に利用可能だが、これを標準機能へと格上げする狙いがある。このほか、デスクトップ向けのデフォルトレンダラーとして「Impeller」が採用されたほか、UIコンポーネントをコード変更なしに確認できる「Widget Previews」機能が安定版として提供開始された。

## 背景と今後の展望

今回のアップデートは、2026年秋に登場予定のiOS 27・macOS 27への対応準備という側面も持つ。あわせてIntel Mac向けサポートの段階的な廃止も始まっており、Appleのプラットフォーム移行に合わせたFlutterのロードマップ再編が進んでいることがうかがえる。UIライブラリのモジュール化とWebAssembly標準化という2つの方向性は、Flutterがプラットフォームごとの差分吸収とパフォーマンス向上を同時に追求する戦略の一環であり、開発者はより柔軟にプラットフォーム対応や描画性能の最適化を行えるようになると期待される。
