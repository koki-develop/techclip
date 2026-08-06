---
date: "2026-08-06T14:56:50+09:00"
title: "GitHub、GitLabからの移行ツール「GitHub Enterprise Importer」を正式提供開始"
description: "GitHubがGitLabからGitHub Enterprise Cloudへリポジトリを移行する公式ツール「gh gl2gh」を一般提供(GA)にした。"
tags:
  - OSS
references:
  - "https://github.blog/changelog/2026-08-03-migrate-from-gitlab-to-github-with-github-enterprise-importer/"
---

## 概要

GitHubは8月3日、GitLabからGitHub Enterprise Cloudへのリポジトリ移行を支援する「GitHub Enterprise Importer」のGitLab対応機能を一般提供(GA)に移行したと発表した。これまでプレビュー段階だった機能が正式版となり、`gh gl2gh`というコマンドラインツールの拡張機能を通じて、GitLab.comおよびGitLab Self-Managed環境からGitHubへの移行を自動化できるようになった。エンタープライズ規模での開発基盤の統合や、複数のバージョン管理サービスを利用している組織の一本化ニーズに応える機能といえる。

## 技術的な詳細

GitHub Enterprise Importerは、単一リポジトリの移行だけでなく、スクリプトを用いた複数リポジトリの一括移行にも対応する。移行時のデータアーカイブの保存先は柔軟に選択でき、GitHub所有のBlobストレージのほか、AWS S3やAzure Blob Storageといった外部ストレージを利用することも可能だ。これにより、組織のセキュリティポリシーやデータ管理方針に応じた移行運用がしやすくなっている。

なお、移行先はGitHub Enterprise Cloud上のgithub.comまたはghe.comに限定されており、オンプレミス版であるGitHub Enterprise Serverへの直接移行には対応していない点は留意が必要だ。移行元についても、gitlab.comおよび現行でサポートされているバージョンのGitLab Self-Managedが対象となる。

## 導入方法

詳細な移行手順は、GitHubが公開している公式ドキュメント「Migrating from GitLab to GitHub」で案内されている。大規模な移行や複雑な要件を抱える組織向けには、GitHubの「Expert Services」チームによる専門的な支援も用意されており、移行計画の策定から実行までのサポートを受けられる。
