---
date: "2026-09-01T18:15:37+09:00"
title: "AstroがProject Steward交代を発表、v7.2ではブラウザ完結の「Astro Playground」を公開"
description: "AstroプロジェクトがProject StewardをFred SchottからMatthew Phillipsに交代したと発表し、同時にAstro 7.2をリリース、ブラウザ上でAstroコンポーネントを試せる新ツール「Astro Playground」などを追加した。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://astro.build/blog/whats-new-august-2026/"
---

## Project Stewardの交代

Astroプロジェクトは8月31日公開の月次アップデートで、Project StewardをFred SchottからMatthew Phillipsに交代したことを発表した。Matthew Phillipsは就任にあたり、「このコミュニティがAstroを素晴らしくしている」とコメントし、これまでプロジェクトを率いてきたFredの功績に謝意を示している。Cloudflareに勤務するPhillipsは、GitHub上のissueをゼロ件まで減らす「ソフトウェアファクトリ」的な運用体制を構築したと報告しており、開発体制の効率化にも取り組んでいることがうかがえる。

## Astro 7.2の新機能

同時にリリースされたAstro 7.2では、実験的な「インクリメンタル静的ビルド」が追加された。変更のあったページのみを再ビルド対象とすることでビルド性能の向上を狙う機能で、まだ実験的フラグの扱いだが、大規模な静的サイトのビルド時間短縮につながる可能性がある。このほか、`astro preview`コマンドにバックグラウンドモードが追加され、プレビューサーバーを別プロセスとして起動できるようになったほか、ロガーのエントリーポイントを相対パスで指定できるようになるなど、開発体験まわりの細かな改善も盛り込まれている。

## Astro Playgroundの登場

今回の目玉のひとつが、Emanuele Stoppaが開発した新ツール「Astro Playground」だ。ブラウザ上でAstroコンポーネントを試せるツールで、セッションごとに実際のAstro Compilerのインスタンスを独立したDynamic Worker上で起動する設計になっている。これにより、ブラウザ上での実行結果がローカル環境でのビルド結果と完全に一致することを担保しているという。UI自体はSvelteで構築されており、ドキュメント参照やちょっとした検証のために手元でプロジェクトをセットアップする手間を省ける点が特徴だ。

## エコシステムの広がり

コミュニティ側の動きとしては、ImageKitがAstro向けの画像最適化統合をリリースしたほか、CloudCannonが多言語対応サイト向けのAstroスターターテンプレートを公開するなど、周辺エコシステムの拡充が続いている。また、SEOおよびAEO(Answer Engine Optimization)向けの統合ツールも複数登場しており、Astroが検索エンジン最適化やAI検索対応の分野でも採用が広がっていることを示している。Steward交代という節目を経て、Astroチームは引き続きビルド性能や開発者体験の改善に注力していく方針とみられる。
