---
date: "2026-10-03T18:12:55+09:00"
title: "SvelteKit 3.0が正式リリース、設定をvite.config.tsへ統合し$libを#libへ置き換え"
description: "SvelteKit 3.0が正式にリリースされ、設定ファイルのvite.config.tsへの統合や$libエイリアスの#lib化など複数の破壊的変更が加わった。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://svelte.dev/blog/sveltekit-3-is-here"
  - "https://www.infoq.com/news/2026/09/sveltekit-3-vite/"
  - "https://dev.to/jamilxt/sveltekit-3-just-shipped-here-is-your-migration-checklist-1ag"
---

## 概要

Svelteの公式フルスタックフレームワーク「SvelteKit」の3.0が10月1日に正式リリースされた。今回のメジャーアップデートは新機能の追加よりもコードベースの整理と基盤強化に重点が置かれており、従来の`svelte.config.js`を廃止して設定を`vite.config.ts`のプラグインオプションへ完全統合したことが最大の変更点となる。この移行はSvelteKit 2.62から段階的に進められてきたもので、Viteプラグインが非同期の設定解決を待たずに同期的に設定を読み込めるようになる。あわせて、`$lib`エイリアスがNode.js標準のサブパスインポート（`package.json`内で定義）を用いた`#lib`に置き換えられるなど、複数の破壊的変更が加わっている。アップグレードにはNode v22.17以上、TypeScript v6以上、Svelte v5.56.4以上、Vite v8.0.12以上、`@sveltejs/vite-plugin-svelte` v7以上が必要で、Vite 8が採用するRolldownバンドラーによりビルドの高速化も見込まれる。

## 破壊的変更とその反応

`#lib`への変更では、インポート時に拡張子を省略できなくなる点が実務上の大きな注意点だ。たとえば従来の`$lib/foo`は`#lib/foo.ts`のように明示的な拡張子付きで記述する必要があり、既存コードベース全体で拡張子なしの解決パターンを置き換える作業が発生しうる。この変更についてはコミュニティでも賛否が分かれており、Redditでは「`$app`など他のエイリアスと一貫性がなくなる」と不満を示す開発者がいた一方、「`package.json`のネイティブなエイリアス定義を使えるようになるため、SvelteKitなしでも動かしたいlib/server系のコードでエイリアスを使える」という利点を指摘する声もあった。メンテナーのRich Harrisも拡張子必須化について「ユーザーが反発するかもしれない」と認めつつ、必要であれば独自のエイリアスを定義する代替手段があるとコメントしている。なお、`preloadStrategy`は今回の整理で削除された一方、`prerender.origin`は`paths.origin`へ、`csrf.checkOrigin`は`csrf.trustedOrigins`へとそれぞれ名称・仕組みが置き換えられた。

## 開発者体験の改善点

破壊的変更以外にも、型安全性の強化や不要な複雑さの削減、エラーハンドリングの改善など開発者体験に関わる変更が多数含まれる。Svelte 5のレンダーエラーに対する実際のエラーバウンダリが有効になり、`+error.svelte`コンポーネントがロード・レンダー双方の失敗を処理できるようになった。すべてのエラーが`handleError`フックを一貫して通過するようになり、本番環境のスタックトレースにもソースマップが反映される。環境変数は実験的ステータスを脱し、`src/env.ts`での明示的な宣言とZodなどStandard Schema準拠ライブラリによる任意の検証が可能になった。ナビゲーション関連では、`pushState`・`replaceState`が非推奨となり`goto`に`shallow: true`オプションを渡す形へ移行、`invalidateAll`は`refreshAll`に改称された。さらに、外部リダイレクトには明示的な`{ external: true }`指定が必須になるなど、挙動の細かな変更も加わっている。`tsconfig.json`も生成済みの`.svelte-kit/tsconfig.json`ではなく`$app/tsconfig`を拡張する形に変わり、従来の多くのコンパイラオプションが不要になる見込みだ。

## 移行方法と今後の展望

移行作業は`npx sv migrate sveltekit-3 --tasks all --confirm`コマンドで自動化でき、手動対応が必要な項目はTODOリストとして出力される。新規プロジェクトは`npx sv create my-new-app`で作成可能だ。公開された移行チェックリストでは、先に最新の2.x系にアップグレードしてから移行を行うことで、破壊的変更に直結する非推奨警告を事前に把握できると推奨されている。開発チームは、Reactのサーバーアクションに類似したセキュアで型安全なクライアント・サーバー間通信を実現する「Remote Functions」を今後の最優先事項としているが、これはAsync Svelteの実験的フラグを前提とするため現時点では引き続き実験的機能にとどまる。チームはこの機能により既存の`load`関数や`actions`が「やや冗長に見える」ようになると述べており、将来的にはデータ取得の中心的な手段として位置づけられる可能性がある。なお、Svelteは11月19〜20日にスロベニア・リュブリャナで開催される「Svelte Summit 2026」で10周年を迎える予定だ。
