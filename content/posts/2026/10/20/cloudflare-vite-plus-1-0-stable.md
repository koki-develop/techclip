---
date: "2026-10-20T18:13:58+09:00"
title: "Cloudflare傘下のVite+が1.0到達、GitLab CI対応とtsup移行パスで本番運用へ準備完了"
description: "CloudflareがVoidZeroを買収して開発を続ける統合JavaScriptツールチェーン「Vite+」が正式版1.0をリリースし、GitLab CI対応やHooks機能、tsupからの移行コマンドを追加した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://www.infoq.com/news/2026/10/cloudflare-viteplus-stable/"
---

## 概要

Vite作成者のEvan Youが創設したVoidZeroが開発する統合JavaScriptツールチェーン「Vite+」が、正式版1.0に到達した。VoidZeroはCloudflareに買収されており、Vite+はその傘下でMITライセンスのもと開発が継続されている。単一の`vp`コマンドからNode.js本体、パッケージマネージャー、Vite 8、Vitest、Oxlint、Oxfmt、Rolldown、tsdownといった複数のツールを一元管理できる点が特徴で、プレビュー版から本番運用に向けた機能拡充を経て今回の安定版リリースに至った。

## 1.0での新機能

今回の1.0では、CI/CD環境への対応が大きく拡張された。GitLab CI/CD向けに`setup-vp`アクションが新たに利用可能になり、GitHub Actionsに限らず主要なCIパイプラインに組み込めるようになった。配布面でもHomebrewとDockerイメージが追加され、導入のハードルが下がっている。

既存プロジェクトからの移行を助ける`vp migrate`コマンドは、tsupプロジェクトへの対応を追加した。実行前に変更内容をプレビュー表示する仕組みも備えており、ビルド設定を壊さずに段階的な移行を進められる。診断系のサブコマンドも充実し、`vp toolchain`で各ツールの正確なバージョンを確認でき、`vp env doctor`はランタイムの解決過程を詳細に説明する。さらに`vp hooks`によってGitフックの管理も`vp`から一元的に行えるようになった。パフォーマンス面では、OxcのネイティブReact Compiler対応により、従来のBabelプラグイン経由の処理に比べて最大10倍の高速化が実現されたという。

## 採用状況と評価

Tiptap、Dify、Hono、BlockNoteといったプロジェクトが既にVite+を採用しており、月間ダウンロード数は約200万件、2,600以上のGitHubリポジトリが依存するまでに広がっている。開発者コミュニティからは、Pythonのパッケージマネージャーかつツールチェーンである`uv`に相当するJavaScript版という評価が出ており、複数の開発ツールを個別にインストール・管理する煩雑さを解消する存在として受け止められている。一方で、ファイルシステム階層の複雑さや、Vite本体の頻繁なメジャーバージョンアップへの追従が課題として指摘されている。

## 今後の展望

VoidZeroはリモートキャッシングやモノレポ向け診断機能の強化を今後の計画として挙げており、リリース作業を支援する`vp release`やドキュメント生成を担う`vp docs`コマンドの追加も予定している。Cloudflareの支援を受けたことで開発体制が強化された形であり、JavaScript/TypeScriptのビルドツールチェーンの標準化がさらに進むかどうか、今後のロードマップの実行が注目される。
