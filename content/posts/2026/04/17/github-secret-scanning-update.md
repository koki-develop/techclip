---
date: "2026-04-17T10:38:05+09:00"
title: "GitHubシークレットスキャン強化：CloudflareがパートナーとなりPush Protection対象パターンを大幅拡充"
description: "GitHubがシークレットスキャン機能を強化し、CloudflareのAPIキー検出を新たに追加するとともに、FigmaやGoogle Cloud Platformなど9種のパターンをPush Protectionのデフォルトブロック対象に拡大した。"
tags:
  - OSS
  - Security
references:
  - "https://github.blog/changelog/2026-04-14-secret-scanning-pattern-updates-and-product-improvements/"
---

## 概要

GitHubは2026年4月14日、シークレットスキャン機能の大規模なアップデートを発表した。最大のトピックはCloudflareとの新たなパートナーシップで、`cloudflare_account_api_token`・`cloudflare_global_user_api_key`・`cloudflare_user_api_token`の3種類のシークレットタイプが検出対象に加わった。これらはパブリック・プライベートリポジトリの両方でPush Protectionがデフォルト有効となっており、誤ってコミットされるのをプッシュ時点でブロックする。

Push Protectionの対象パターンも大幅に拡充された。新たにデフォルトでコミットをブロックするパターンとして、FigmaやGoogle Cloud Platform（GCP）、Langchain、OpenVSX、PostHogなど9種のシークレットが追加された。これらはOrganizationの管理者が設定でカスタマイズすることも引き続き可能だ。

## EMUフォーク継承とAPIの改善

エンタープライズ向けの重要な機能改善として、EMU（Enterprise Managed Users）環境のフォークにおけるPush Protection継承が強化された。これまではフォーク先のリポジトリでシークレット保護が引き継がれないケースがあったが、今回の更新により「ユーザー所有のフォークは、最も近いライセンス済み祖先リポジトリからPush Protectionを継承する」仕組みとなり、フォークを経由した保護のすり抜けが防止される。

APIレベルでも複数の改善が加えられた。カスタムパターンのアラートに対して、PATCH エンドポイントを通じて `active`・`inactive` などの有効性ステータスを手動で設定・リセットできるようになった。また、アラート取得APIのレスポンスに `provider` および `provider_slug` フィールドが追加され、`providers` や `exclude_providers` クエリパラメータを使ったプロバイダー単位のフィルタリングがエンタープライズ・Organization・リポジトリの各エンドポイントで利用できるようになった。

## スキャン履歴と管理機能の強化

スキャン履歴APIにも新機能が追加された。AIを活用した汎用シークレットのバックフィルスキャンの結果が、新たな `generic_secrets_backfill_scans` 配列としてAPIレスポンスに含まれるようになり、どのスキャンが実行されたかを履歴として参照できる。さらに、エンタープライズオーナーおよびセキュリティ管理者が全Organizationにわたるシークレットスキャンの却下リクエストを一覧できる新エンドポイントも追加された。Organization・レビュアー・ステータスによるフィルタリングに対応しており、大規模環境での監査・管理業務を効率化する。シークレットスキャンキャンペーン機能にもチームおよびトピックによるフィルタリングが追加され、コードスキャンキャンペーンと同等の絞り込み機能が利用できるようになった。
