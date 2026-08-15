---
date: "2026-08-15T20:02:43+09:00"
title: "Jetpack Compose 1.12が安定版に、メッシュグラデーションと広色域対応を追加"
description: "GoogleがAndroid向けUIツールキットJetpack Compose 1.12を安定版としてリリースし、メッシュグラデーションや広色域・HDR対応、Gridの名前付きレイアウト領域、Credential Manager統合などを追加した。"
tags:
  - Programming Languages
references:
  - "https://android-developers.googleblog.com/2026/08/jetpack-compose-august-2026-release.html"
---

## 概要

Googleは2026年8月12日、Android向けUIツールキット「Jetpack Compose」のバージョン1.12を安定版としてリリースした。Compose BOM（Bill of Materials）は`androidx.compose:compose-bom:2026.08.00`に更新される。今回のリリースでは、グラフィックス表現力の強化、レイアウトAPIの拡充、テキスト編集・選択まわりの機能追加、そしてランタイム性能の改善など、多岐にわたる変更が含まれている。なお対象compileSdkはAPI 37となり、AGP（Android Gradle Plugin）は9.1.1以上が最小要件となる点には注意が必要だ。

## グラフィックスとレイアウトの強化

目玉機能の一つが、新たに導入された`MeshGradientPainter`によるメッシュグラデーション対応だ。開発者はグリッド状の行・列に沿って頂点位置と色を定義することで、複数の色が滑らかに補間される有機的なグラデーション表現を作成できる。あわせて、Display P3などの広色域（WCG）やHDRレンダリングのフルパイプライン対応も追加された。非sRGB色域の色は色のクランプ（丸め）なしにプラットフォームのレンダリングを通して保持され、非対応の色空間やAndroid 9以下の端末では自動的にsRGBへフォールバックする。また、`GraphicsLayer`と`Modifier.graphicsLayer`には`LayerOutsets`が加わり、測定サイズを超えて視覚的な描画範囲を拡張できるようになった。

レイアウト面では、実験的機能である`Grid`コンポーネントが名前付きレイアウト領域に対応した。従来の数値インデックスの代わりに、`GridConfigurationScope`で意味のある名前付き領域を定義し、`gridItem(areaId = "name")`で配置できるようになったことで、複雑な2Dレイアウトの記述が簡潔になる。アニメーション面でも、ジェスチャー駆動のインタラクティブな2段階トランジションを実現する`DeferredAnimatedContent`・`DeferredAnimatedVisibility`が追加され、`DeferredTargetAnimation`は実験的ステータスを卒業して正式機能となった。

## テキスト編集とCredential Manager統合

`BasicTextField`では、`TextFieldBuffer`スコープの`addStyle()`メソッドによりインライン`SpanStyle`・`ParagraphStyle`を適用できるようになり、編集可能なリッチテキスト書式設定に対応した。`getSpanStyles()`や`getParagraphStyles()`で書式情報を取得できるほか、新設された`SelectionState` APIにより`SelectionContainer`のテキスト選択をプログラムから制御できる（`selectAll()`、`select(TextRange)`、`extendSelectionByWord()`など）。

さらに注目すべきは、Android のCredential Manager（API 34以上）とのシームレスな統合だ。テキストフィールドがAutofillフレームワーク経由で連携し、新たな`credentialRequest`セマンティクスプロパティと`CredentialRequestData`を用いることで、パスキーや保存済み認証情報の入力を直接プロンプト表示できる。このほか、ダウンロード可能フォントのフォントバリエーション設定対応、テキスト選択ドラッグ時の自動スクロール、`KeyboardType`への`Date`・`Time`・`DateTime`・`SignedDecimal`の追加なども盛り込まれた。

## パフォーマンスとテスト機能の改善

ランタイム面では、コルーチンを必要としない単発エフェクト向けにキー引数を受け取れる`SideEffect`のオーバーロードが追加され、`LaunchedEffect`比で最大90%、`DisposableEffect`比で約20%高速というベンチマーク結果が示されている。また起動時最適化も進み、初回フレーム描画までの時間（Time to Initial Display）は従来のView実装と同等の水準に達したという。テスト面でも、UIの保留中の作業をクロックを進めずに確認できる`hasPendingWork()`や、手動でのクロック制御中に暗黙的な同期を無効化する`runWithoutImplicitWait()`など、より細かい制御を可能にするAPIが追加された。

## 今後の展望

開発者向けの移行作業としては、Compose BOMを`2026.08.00`に更新し、compileSdkをAPI 37へ、AGPを9.1.1以上に引き上げる必要がある。また、非推奨となった`Modifier.onFirstVisible()`は、より精度の高い可視性トラッキングを提供する`Modifier.onVisibilityChanged()`へ置き換えることが推奨されている。なお、デザインシステム向けの新API「Styles API」は、型安全性や正確性、カスタムデザインシステムのサポートを確立するための基盤設計を固める段階にあり、引き続き実験的ステータスのまま開発が続けられる予定で、今後も破壊的変更が見込まれるとしている。
