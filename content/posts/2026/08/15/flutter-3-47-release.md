---
date: "2026-08-15T08:03:19+09:00"
title: "Flutter 3.47リリース、Material/Cupertino UIが1.0到達しデスクトップのImpellerが標準に"
description: "GoogleがFlutter 3.47をリリースし、Material/Cupertino UIパッケージの1.0到達やデスクトップ環境でのレンダリングエンジンImpellerのデフォルト化など、安定性と開発体験の向上を図った。"
tags:
  - Programming Languages
references:
  - "https://flutter.dev/blog/whats-new-in-flutter-3-47"
---

## 概要

Googleは8月12日、クロスプラットフォームUIフレームワークFlutterの新バージョン3.47をリリースした。今回の目玉は、UIウィジェット群であるMaterial UIとCupertino UIパッケージが正式に1.0へ到達し、コアSDKから分離されたことだ。これにより開発者はFlutter SDK本体をアップグレードすることなく、最新のMaterialおよびCupertinoウィジェットのスタイルを個別に利用できるようになった。移行は`dart fix --apply --code=migrate_design_widgets`コマンドで自動化されており、既存プロジェクトも比較的スムーズに対応可能だ。

## デスクトップ向けレンダリングエンジンImpeller

次世代レンダリングエンジンImpellerが、macOS・Windows・Linuxのデスクトップ環境でデフォルトのレンダラーとなった。Impellerは実行時のシェーダーコンパイルを排除する設計になっており、アプリ起動直後の初フレームからシェーダーコンパイルに起因するカクつきがなく、滑らかなアニメーション体験を実現する。あわせてデスクトップでのテキストレンダリングにSignedDistanceFunction方式が採用され、より鮮明な文字表示が可能になった。

## プラットフォーム別の変更

iOS/macOSでは対応バージョンの引き上げが行われ、iOSの最小対応バージョンは13から15へ、macOSは10.15から12へと変更された。あわせてiOS 27 SDK対応として、UISceneライフサイクルの採用が必須となる。macOSではApple Silicon移行の推進に伴い、Intel Macに対する自動テストが廃止された。またSwift Package Managerへの移行も進んでおり、利用の多いiOSプラグイン上位100件のうち92件が既に移行を完了しているという。

## パフォーマンスと開発者体験の改善

WebAssembly対応では`--wasm`フラグによる有効化に加え、実験的機能として遅延ローディング(`--enable-wasm-deferred-loading`)がサポートされた。開発者向けにはWidget Previewにローカルキャッシング機能が導入され、`.widget_preview/`フォルダの活用によってセットアップ時のオーバーヘッドが削減されている。デスクトップでは複数ウィンドウ機能が強化され、ポップアップウィンドウのサポート、ウィンドウハンドルのクエリ機能、サイズ自動調整APIが新たに追加された。Androidでは仮想キーボードの修飾キーが固着する不具合も修正されている。

## 破壊的変更と今後の展望

一方で、`flutter_localizations`パッケージがコアSDKからアンバンドルされ、`GlobalMaterialLocalizations.delegates`を用いた新形式への移行が必要になる点には注意が必要だ。コアSDK内に残る設計ライブラリは11月予定のFall安定版で正式に廃止される見込みで、開発者は早めの移行が求められる。Googleは今後、WebAssemblyのデフォルト化やImpellerフォールバックの廃止、SwiftPMへの完全移行をさらに推進していく方針を示しており、Flutterのプラットフォーム基盤は今後も継続的に刷新されていく見通しだ。
