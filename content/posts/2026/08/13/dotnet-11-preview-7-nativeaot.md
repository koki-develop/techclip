---
date: "2026-08-13T08:12:37+09:00"
title: ".NET 11 Preview 7がリリース、CLIでNativeAOTが標準有効化されC# 15にユニオンパターンも追加"
description: "Microsoftが.NET 11 Preview 7を公開し、dotnet CLIでのNativeAOTデフォルト有効化やC# 15の新パターンマッチング機能などを追加した。"
tags:
  - Programming Languages
references:
  - "https://devblogs.microsoft.com/dotnet/dotnet-11-preview-7/"
  - "https://www.infoworld.com/article/4208694/microsoft-rolls-out-dotnet-11-preview-7.html"
  - "https://www.neowin.net/news/microsoft-launches-net-11-preview-7-with-c-upgrades-and-faster-builds/"
---

## 概要

Microsoftは8月11日、.NET 11の7番目のプレビュー版となる「.NET 11 Preview 7」を公開した。今回の目玉は、`dotnet` CLIにおけるNativeAOTのデフォルト有効化だ。NativeAOTはアプリケーションをネイティブコードへ事前コンパイルする仕組みで、これまではオプトインの機能だったが、Preview 7からはCLI経由での利用時に標準で有効になる。あわせてMSBuildサーバーもデフォルトで有効化され、ビルドのパフォーマンス向上が図られている。.NET 11の正式リリースは2026年11月を予定しており、SDKはdotnet.microsoft.comから、あるいはVisual Studio 2026 Insidersをインストールすることで試用できる。

## C# 15の新機能

言語面ではC# 15に新しいパターンマッチング機能が加わった。「ユニオンパターン」はユニオン型そのもの、またはその値のいずれにもマッチできる「Try-Both」方式のマッチングアプローチを採用しており、より柔軟な条件分岐の記述が可能になる。また、ラベル付き`break`文とラベル付き`continue`文がサポートされ、ネストしたループの外側から直接抜け出したり、特定のループへ制御を戻したりできるようになった。型パラメータが閉じた型に制限されている場合の網羅性チェックも改善されており、パターンマッチングの安全性が高まっている。

## ランタイムとツールチェーンの改善

ランタイム面では、非同期メソッドのコンパイル方式が刷新された。従来「ランタイム非同期」はコンパイル速度を優先したTier 0コードのみで実行されていたが、Preview 7からは段階的コンパイルパイプラインを通じてコンパイルされるようになり、実行時のパフォーマンス向上が期待できる。また、CoreCLRのWebAssembly対応も進展しており、Preview 6での起動成功に続き、Preview 7ではCoreCLRライブラリのテストスイートをエンドツーエンドで実行できるようになったと報告されている。

ツールチェーン面では、`dotnet test`コマンドに`--timeout`と`--maximum-failed-tests`オプションが追加され、CI環境などでテスト実行を柔軟に制御できるようになった。MAUI、Android、iOS向けのテスト機能拡張や、Blazorアナライザーの5種類の追加、HTTPコンテンツの圧縮ラッパー(GZip、Brotli、Zstandard)対応なども盛り込まれている。このほか、ライブラリではIEEE 754準拠の10進浮動小数点型がサポートされ、ASP.NET CoreのBlazorでは回路の自動一時停止機能が、Entity Framework Coreではクエリ変換の改善が、Windows Formsでは視覚スタイルの改善が行われている。

## 今後の見通し

.NET 11は2026年11月の正式リリースに向けて開発が進んでおり、今回のPreview 7はその重要なマイルストーンの一つとなる。NativeAOTのCLIデフォルト化は、起動速度やデプロイサイズを重視する開発者にとって特に注目される変更であり、正式版までにさらなる安定化や対応範囲の拡大が見込まれる。C# 15の新パターンマッチング機能についても、正式リリースまでにフィードバックを踏まえた調整が加えられる可能性がある。
