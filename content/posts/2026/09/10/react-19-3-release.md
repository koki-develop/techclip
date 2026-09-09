---
date: "2026-09-10T08:11:04+09:00"
title: "React 19.3リリース、ViewTransitionとFragment Refsが正式版に昇格"
description: "React 19.3が公開され、ViewTransitionとFragment Refsが実験的APIから安定版に昇格したほか、browser()関数によるサーバーレンダリングの選択的スキップやTrusted Types対応が追加された。"
tags:
  - Programming Languages
references:
  - "https://react.dev/blog/2026/09/09/react-19-3"
---

## 概要

Reactチームは9月9日、バージョン19.3をnpmで公開した。目玉は`<ViewTransition>`と`Fragment`へのref対応（Fragment Refs）が実験的APIから正式に安定版へ昇格したことで、これに加えてサーバーレンダリングを選択的にスキップする`browser()`関数、Trusted Types対応の改善、Server Componentsでのcontext直接描画など、実用面での改善が多数盛り込まれた。あわせてFast RefreshやServer Components、フォーカス管理まわりで報告されていた多数の不具合も修正されている。

## ViewTransitionとFragment Refsの安定化

`<ViewTransition>`はブラウザのView Transition APIを利用してUIのアニメーションを実装するコンポーネントで、`startTransition`でマークされた更新、`<Suspense>`のreveal、`useDeferredValue`による更新をアニメーション化する（緊急の更新はアニメーション化されない）。要素の追加（enter）・削除（exit）・内容変更（update）・名前付き要素の移動（share）の4種類のトリガーに対応し、`addTransitionType`と組み合わせることでカルーセルの前進・後退のように同じ状態更新でも異なるアニメーションを出し分けられる。`<Suspense>`と組み合わせた場合はフォールバックを即座に表示しつつ最終コンテンツへの切り替えだけをアニメーションさせるパターンが推奨されており、`update="auto" default="none"`という設定例が示されている。現時点ではDOM環境のみのサポートで、React Native等への対応は今後の課題とされている。

もう一つの目玉であるFragment Refsは、`<Fragment>`に直接refを渡せるようにする機能だ。従来、親要素を持たない兄弟要素の集合や、refを公開しないライブラリコンポーネントの中身を操作する手段がなかったが、Fragment Refsで得られる`FragmentInstance`はイベントリスナーの追加・削除、深さ優先探索によるフォーカス管理（`focus`/`focusLast`/`blur`）、`IntersectionObserver`や`ResizeObserver`の接続、`getClientRects`によるサイズ測定などをコンポーネント内部を変更せずに実現できる。

## browser()関数とTrusted Types対応

サーバーレンダリング環境では同じコンポーネントがサーバーとクライアントの両方で実行されるため、`localStorage`やローカルタイムゾーンなどブラウザ固有の情報に依存する処理はサーバー側で意味のある出力を生成できないという課題があった。従来は`useEffect`でマウント状態を管理したり`typeof window`を判定したりする回避策が使われてきたが、React 19.3では`use(browser())`を呼ぶことでサーバーレンダリングを明示的にオプトアウトできるようになった。サーバー側ではSuspenseをトリガーして最寄りのフォールバックをHTMLとして出力し、クライアント側では通常通りレンダリングされる。`use`の他の呼び出しと同様に条件分岐や早期リターンの後でも使用できるため、propsにデフォルト値がある場合だけサーバーレンダリングを許可するといった柔軟な制御も可能だ。

セキュリティ面では、DOM型XSS攻撃を防ぐTrusted Types APIへの対応が改善された。従来Reactは値を`'' + value`のように文字列へ強制変換してからDOM APIへ渡していたため、`TrustedHTML`などの型付きオブジェクトが平文文字列に戻されてブラウザに拒否される問題があったが、19.3では値を強制変換せず直接渡すよう修正され、`require-trusted-types-for 'script'`ポリシーが意図通り機能するようになった。またServer Componentsでは、これまで`'use client'`側でProviderコンポーネントをラップする必要があったcontextの受け渡しが、`<UserContext value={...}>`のように直接記述できるようになり、ボイラープレートが削減されている。

## パフォーマンス改善と主なバグ修正

パフォーマンス面では、複数のTransitionが1つのレンダーに絡み合い、低速なTransitionが無関係な更新まで遅延させていた問題を解消し、Transitionが独立してレンダリングされるよう改善された。また`resize`イベントからの更新が次フレームまでバッチ処理されるようになったほか、`onFullscreenChange`/`onFullscreenError`イベント、SVGの`maskType`属性、iframeの`credentialless`属性、モジュールリソースの`fetchPriority`などにも対応した。

バグ修正では、`useDeferredValue`が古い値のままスタックする不具合、Suspenseフォールバックへのcontext伝播の不備、非表示ツリー内でデハイドレーションされたSuspense境界を更新した際にハングする問題、`<Activity>`が非表示になった後も`<title>`が`<head>`にホイストされ続ける問題などが修正された。React DOM側ではMobile Safariでの`<ViewTransition>`クラッシュや`SuspenseList`との組み合わせでのクラッシュ、フォーカス管理の不具合が解消され、React Server側では深い非同期呼び出しチェーンでのスタックオーバーフローや`Error.cause`・`AggregateError.errors`のクライアントへの転送不備なども修正されている。Reactチームは今後もView TransitionsのReact Native対応を進めるとしている。
