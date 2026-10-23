---
date: "2026-10-24T08:11:12+09:00"
title: "Cloudflare、TypeScriptコンパイラのRust移植「tsrs」を発表 最大8倍高速化、エージェントが開発を主導"
description: "CloudflareがVoidZeroやTypeScriptチームと協力し、TypeScriptコンパイラをRustに移植した「tsrs」を発表、最大8倍の高速化とメモリ使用量70%削減を実現した。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://blog.cloudflare.com/typescript-rust-port"
  - "https://thenewstack.io/cloudflare-rust-typescript-tsrs/"
---

## 概要

Cloudflareは10月20日、TypeScriptコンパイラをRustに移植したプロジェクト「tsrs」を発表した。VoidZeroおよびOwner.comのMax Schwenk氏、そしてTypeScriptチーム自身と協力して進められており、JavaScript向けコンパイラ・ツールチェーンである「Oxc」の一部として育成していく計画だ。ベンチマークでは、すでにリリース済みのTypeScript 7.0と比較して最大8倍の処理速度向上、メモリ使用量は約70%削減という結果が示されている。なお、この高速化の一部はすでにベータ版が公開されているTypeScript 7.1にも還元されており、同ベータ版はTypeScript 7.0と比較して最大2.5倍高速化しているという。TypeScriptチームと「同一条件での比較」を確認し合うなど、測定の信頼性にも配慮している。

## フォークではなく忠実な移植を目指す方針

プロジェクトの最大の特徴は、"We are not forking TypeScript"(TypeScriptをフォークするものではない)と明言している点だ。言語仕様や設計の完全な統制権はあくまでTypeScriptチームが持つべきだという立場を取り、tsrsは独自路線を歩む新しい処理系ではなく、既存のTypeScriptに忠実な代替実装として位置づけられている。この方針には、言語の長期的なビジョンを損なわず、既存エコシステムとの互換性を保証する狙いがある。

## RustとWebAssemblyを選んだ理由

実装言語にRustを選んだ背景には、WebAssembly対応への強いこだわりがある。Goのような言語はランタイムにガベージコレクタを同梱する必要があるのに対し、Rustのメモリ管理モデルはWebAssembleのゲストとホスト間で直接的なメモリ相互作用を実現でき、効率面で優位になるという。すでにNext.js互換レイヤー「Vinext」で培った知見も活用される見込みで、移植作業そのものの多くはAIエージェントによって担われたという点も注目される。

## 継続的なメンテナンス体制と今後の展開

tsrsはOxcの一部として継続的に保守される予定で、Vinextで実績のある運用モデルを踏襲する。具体的には、エージェントによる日次レビュー、アップストリーム(本家TypeScript)との差分取得、互換性マトリックスの自動再生成を組み合わせることで、本家との乖離を最小限に抑える体制を構築するとしている。今後はTheo Browne氏が手がける「tsc-rs」との統合、型を認識したルールのOxlintへの統合、さらには安全なサンドボックス環境内での開発ツールチェーン実行なども計画されており、Rust・WebAssemblyベースの高速なTypeScriptエコシステム構築に向けた取り組みが続く見通しだ。
