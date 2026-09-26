---
date: "2026-09-26T18:12:40+09:00"
title: "Node.js 26.10.0リリース、util.throttle()/debounce()やcrypto.parsePKCS12()をコアに追加"
description: "Node.js 26.10.0が公開され、util.throttle()/debounce()やcrypto.parsePKCS12()などの新APIとSlidingWindowHistogramによるパフォーマンス計測機能の強化が図られた。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://nodejs.org/en/blog/release/v26.10.0"
---

## 概要

Node.jsプロジェクトは9月22日、Currentライン最新版となる「Node.js 26.10.0」を公開した。リリースは@aduh95氏が担当している。今回の目玉は、これまでnpmパッケージに頼らざるを得なかった`util.debounce()`と`util.throttle()`がコアAPIとして取り込まれたことだ。実装を手掛けたJames M Snell氏は、外部パッケージに頼らずとも標準ライブラリに「ただ存在している(Just There)」ことの価値を重視したと述べており、レビュアーのMatteo Collina氏も「ほぼすべてのアプリケーションで使っている」とその実用性を評価している。加えて`crypto.parsePKCS12()`、`fs.openAsBlobSync()`など、実務でよく使われる機能のコア統合が目立つリリースとなった。

## 主要な新API

`crypto.parsePKCS12()`は、.p12/.pfx形式の証明書バンドルから秘密鍵と証明書、追加の証明書チェーンを一度に取り出せる新関数で、戻り値には`privateKey`・`certificate`・`additionalCertificates`が含まれる。従来はOpenSSLのコマンドラインツールや`node-forge`のようなサードパーティ製ライブラリに頼る必要があった処理を、Node.js単体で完結できるようになる。

ファイルシステム関連では`fs.openAsBlobSync()`が追加され、ファイルを同期的にBlobとして開けるようになった。非同期APIを介さずにWeb標準のBlobインターフェースでファイルへアクセスできる点が特徴だ。またネットワーク周りでは、`net.BoundSocket`をワーカースレッドや子プロセスへ転送できるようになり、SQLiteモジュールでは`undefined`値を渡すとSQLのNULLとして扱われるよう挙動が明確化された。

## パフォーマンス計測とその他の変更

`perf_hooks`にはスライディングウィンドウ方式でレイテンシ分布を追跡する`SlidingWindowHistogram`クラスが実装され、QRDE(Quantile-Respectful Density Estimate、分位点尊重密度推定)による統計分析にも対応した。長時間稼働するサーバーのレイテンシ傾向を、直近の時間枠に絞って観測しやすくなる。あわせて未処理のPromise警告を抑止する`util.markPromiseAsHandled()`も追加されている。

実験的機能である仮想ファイルシステム(VFS)まわりも拡張され、`node:ffi`がマウント済みのVFSから直接ネイティブライブラリを読み込めるようになったほか、不正なFFIパラメータに対するエラーハンドリングも改善された。このほかHTTP/2やstream、TLS、子プロセスなど広範なモジュールにわたる修正が多数含まれており、crypto関連の堅牢化やstreamのバッファ管理まわりの性能改善も行われている。

## 位置づけと今後

26.10.0はLTSではなくCurrentラインのリリースであるため、最新APIをいち早く試せる一方、長期的な安定運用を求める環境ではLTS版への追従が推奨される。今回コアに統合された`util.throttle()`/`debounce()`のように、開発現場で定番となっていたユーティリティを標準ライブラリに取り込む流れは今後も続くとみられ、次期LTS候補への機能反映にも注目が集まる。
