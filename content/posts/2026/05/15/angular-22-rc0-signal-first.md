---
date: "2026-05-15T02:39:39+09:00"
title: "Angular 22.0.0-rc.0リリース、Signal Forms安定化とゾーンレスがデフォルトに——「Signal-First」時代の幕開け"
description: "Angular 22の最初のRelease Candidateが公開され、Signal Formsの安定化、ゾーンレスアーキテクチャのデフォルト化、VitestのCLIデフォルト採用など、「Signal-First」設計への本格移行が示された。"
tags:
  - Programming Languages
references:
  - "https://github.com/angular/angular/releases/tag/v22.0.0-rc.0"
---

## 概要

Googleは2026年5月13日、Angular 22の最初のRelease Candidate（rc.0）を公開した。このリリースは、Angularフレームワークが長年にわたって推進してきた「Signal-First」設計への移行を集大成するマイルストーンとなっている。Signal Formsの安定化、ゾーンレス（Zoneless）アーキテクチャのデフォルト化、そしてVitestをCLIのデフォルトテストランナーとして採用するという3つの大きな変化が同時に実現し、Angularアプリケーションの構築方法そのものが刷新される。

## Signal Formsの安定化

Angular 21で実験的機能として導入されたSignal Formsが、v22でついに安定版となった。従来のReactive FormsやTemplate-Driven Formsに代わり、Signal Formsはシグナルベースの新しいリアクティブフォームAPIを提供する。`form()`関数がバリデーション機能を持つ`FieldTree`を生成し、`formField`ディレクティブでツリーをInput要素に結合する設計だ。

この仕組みにより「細粒度の更新」が実現される。50フィールドを持つような大規模なフォームでも、変更が発生したフィールドのみが再レンダリングされるため、パフォーマンスが大幅に向上する。バリデーションも`required`や`minLength`などの標準ルールに加え、`validate`関数によるカスタムバリデーションが簡潔に記述できるようになった。

## ゾーンレスアーキテクチャのデフォルト化

Angular 22では、ゾーンレスアーキテクチャが新規プロジェクトのデフォルトになる。従来のZone.jsは圧縮後で約30KBのオーバーヘッドがあり、ブラウザのネイティブAPIに対してモンキーパッチを適用することで変更検出を行ってきた。ゾーンレスではこの仕組みを廃し、シグナルやObservableによる明示的なバインディングで変更を追跡する。

既存プロジェクトでは`provideZoneChangeDetection()`を使ってZone.jsに戻すことが可能だが、新規プロジェクトではゾーンレスが標準となる。また、新しいコンポーネントではデフォルトで`OnPush`変更検出戦略が適用されるようになり、不要な変更検出サイクルが根本的に排除される。

## VitestのCLIデフォルト採用と新APIの追加

テスト環境においても大きな転換が行われた。KarmaとJasmineに替わり、VitestがAngular CLIのデフォルトテストランナーとして正式採用される。Vitestはテストの並列実行やスナップショットテストをサポートし、開発ループをほぼ瞬時にするほどの高速実行を実現する。API面でもJasmineの`spyOn`が`vi.spyOn`形式となり、`fakeAsync`/`tick`の代わりに`vi.useFakeTimers()`を使う形式へ移行する。

また、rc.0では`debounced()` Signalの追加や、セレクタ文字列が不要になるSelectorless Componentsの導入も予定されている。`debounced()`はRxJSを使わずにネイティブなdebouncingを実現し、コードのシンプルさを保ちながらUIの入力最適化が行えるようになる。さらに、Model Context Protocol（MCP）を通じたAIコーディングアシスタントとの連携強化も図られており、Angular CLIがMCPサーバーとして機能する形で、AIツールとのシームレスな統合が実現される予定だ。
