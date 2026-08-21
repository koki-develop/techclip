---
date: "2026-08-22T02:06:56+09:00"
title: "Bun v1.4リリース、コアをRustへ全面移行しCPU使用率5分の1に"
description: "JavaScriptランタイムBunがv1.4をリリースし、コアをZigからRustへ全面書き換え、大幅な性能改善と多数の組み込み機能を追加した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://bun.com/blog/bun-v1.4"
---

## 概要

JavaScriptランタイムのBunが8月20日、v1.4をリリースした。最大の変更点は、約100万行に及ぶコア実装をZigからRustへ全面的に書き換えたことで、これはRust化されたBunとしては最初の正式リリースとなる。開発チームによれば、AIコーディングツールのClaude CodeはすでにRust版のBunを数ヶ月にわたり本番運用しており、Prismaも新製品「Prisma Compute」をこの新しい基盤の上に構築しているという。Rust移行の詳細な技術的背景は別のブログ記事で説明されているが、今回のリリースではこの新基盤の上でメモリ使用量削減やCPU負荷低減、起動時間短縮といった具体的な性能改善が示されている。

## 性能面の改善

ベンチマークでは、Claude Codeの本番環境における計測でCPU使用率がp99で24%から10%に、p50で5.8%から2.5%へと大幅に低下したことが報告されている。アイドル時のCPU使用率は5倍削減され、HTTPサーバのメモリ使用量も13〜48%削減された。起動時間についても、Windowsで2.5倍(15.5ms)、Linuxで2倍(5.1ms)高速化し、バイナリサイズもLinux・Windows向けで最大17%縮小したという。npmパッケージのインストール速度に関しては、T3スタックのNext.jsアプリでの初回インストールが1.41秒となり、npmと比較して15倍高速だったと報告されている。

## 追加された機能

v1.4では15個の外部依存パッケージが組み込み機能として内蔵化された。ヘッドレスブラウザ自動化を可能にする「Bun.WebView」はPuppeteerやPlaywrightを必要とせず、macOSではシステムのWebKitを利用する。画像処理APIの「Bun.Image」は1080pのPNGを400×400のJPEGにリサイズする処理でsharpより1.38倍高速だとされる。このほか、GFMテーブルや打消し線、チェックリストに対応したMarkdownパーサ「Bun.markdown」、OSレベルのスケジューリングと連携する「Bun.cron()」、PTYをサポートしbashやvim、htopを操作可能な「Bun.Terminal」、SIMDを用いたXMLパーサ「Bun.XML」、JSON5・JSONLのパースとストリーミング対応などが新たに加わった。

## Node.js互換性の向上

Node.js互換性の面でも大きく前進しており、Bun 1.0以降で最大となる1,517件の新規テスト合格を達成した。node:http、node:fs、node:cluster、node:timers、node:zlib、node:vmといったモジュールは97%の互換率に達し、node:quicは99%、node:events・node:trace_events・node:sqliteは100%の互換率となっている。worker_threadsのresourceLimitsやstdout/stderr、wsのupgrade・unexpected-responseイベント、node:clusterのソケット共有など新たなAPIサポートも加わり、PlaywrightやNext.js 16、vitest、OpenTelemetry、dd-traceなどが実際にそのまま動作することが確認されている。

## 今後の展望

一方でHTTP/3対応は依然として実験的な位置付けにとどまっており、公式ブログでも本番環境への投入は避けるよう明記されている。HTTP/2・HTTP/3対応のfetchクライアントについても段階的な展開が続けられる方針だ。開発チームはNode.jsの「drop-in replacement」となることを目標に掲げており、互換性テストスイートを全コミットで実行する体制を構築するなど、継続的な互換性強化に取り組んでいくとしている。
