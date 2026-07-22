---
date: "2026-07-23T02:32:22+09:00"
title: "GitHub Actions、「Pwn Request」対策の安全なデフォルト動作を全バージョンへバックポート"
description: "GitHubはactions/checkoutにおいて未レビューのフォークPRコードを拒否する安全なデフォルト動作を、v7だけでなく既存の主要バージョンにもバックポートし、サプライチェーン攻撃「Pwn Request」のリスクを大幅に低減した。"
tags:
  - OSS
  - Security
references:
  - "https://www.techtimes.com/articles/321003/20260720/github-actions-gets-secure-default-ci-cd-backport-shuts-pwn-request-window.htm"
  - "https://github.blog/changelog/2026-06-18-safer-pull_request_target-defaults-for-github-actions-checkout/"
  - "https://thehackernews.com/2026/06/github-updates-actionscheckout-to-block.html"
---

## 概要

GitHubはCI/CDで広く使われる公式アクション`actions/checkout`に、サプライチェーン攻撃「Pwn Request」を防ぐ安全なデフォルト動作を追加し、既存の主要バージョン全体へバックポートした。対象となるのは`pull_request_target`や`workflow_run`イベントで動作するワークフローで、フォークリポジトリの未レビューなプルリクエストのコードをチェックアウトしようとすると、ワークフローを失敗させる仕様に変わった。この変更は`actions/checkout@v4`のようにfloatingタグ（メジャーバージョンのみを指定するタグ）を使っているワークフローには自動的に適用される。当初は7月16日の適用開始が予定されていたが、実際の全面適用は7月20日にずれ込んだ形となった。

## Pwn Requestとは何か

`pull_request_target`イベントは、通常の`pull_request`イベントとは異なり、ベースリポジトリの`GITHUB_TOKEN`や各種シークレット、デフォルトブランチのキャッシュへのアクセス権を持った状態でワークフローが実行される。ここで従来の`actions/checkout`は、指定さえすればフォークPRのヘッドコミットも無条件にチェックアウトしていたため、悪意ある投稿者がPRを送るだけで、レビューされていない攻撃者制御下のコードが昇格した権限で実行されてしまう危険があった。GitHub自身も「未レビューのフォークPRのヘッドをこうしたワークフロー内でチェックアウトすると、通常は攻撃者制御のコードがワークフローの全権限で実行されてしまう」と説明しており、この攻撃パターンは近年、Nx、PostHog、TanStack、Emacsパッケージなどを巻き込んだ複数の実際のサプライチェーン侵害の原因となっていた。

## 技術的な仕組みと対象範囲

新しいデフォルト動作は、`pull_request_target`または`workflow_run`（後者は`workflow_run.event`が`pull_request`系イベントの場合に限る）のワークフロー内で、以下の条件が同時に満たされる場合にチェックアウトを拒否する。

- `repository:`がフォークリポジトリを指し示している
- `ref:`が`refs/pull/<番号>/head`など、PRのヘッドやマージ参照に該当する
- 実際に解決される参照がフォークのヘッドまたはマージコミットSHAである

同一リポジトリ内のPRや通常の`pull_request`イベントは影響を受けない。GitHubは6月18日に`actions/checkout` v7としてこの保護機能を一般公開した後、v1を除く既存の主要バージョン（v2〜v6系統など）にも同等の安全策をバックポートし、フォーク由来の危険なコードチェックアウトを塞いだ。

## 開発者への影響と対応方法

昇格権限が本当に必要な特殊なワークフロー（例えば、レビュー済みのラベルが付いたPRのみを対象とするデプロイパイプラインなど）のために、GitHubは`allow-unsafe-pr-checkout`という入力パラメータを用意しており、これを明示的に指定すればこれまで通りの動作に戻せる。あえて警告的な名前を付けることで、コードレビュー時にこのオプトアウトが目立ち、レビュアーが気づきやすいよう配慮されている。一方で、`actions/checkout`を特定のSHAやマイナー・パッチバージョンにピン留めしているワークフローは自動的には保護を受けないため、Dependabotなどの仕組みを使って明示的にアップグレードする必要がある。今回の変更はCI/CDのデフォルト設定をより安全な方向に倒す取り組みの一環であり、他のGitHub Actions関連ツールでも同様の「secure by default」の流れが今後広がることが予想される。
