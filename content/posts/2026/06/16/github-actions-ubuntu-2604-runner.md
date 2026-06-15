---
date: "2026-06-16T03:37:02+09:00"
title: "GitHub ActionsにUbuntu 26.04とWindows 11 ARM64新ランナーイメージがパブリックプレビュー公開"
description: "GitHub Actionsのホステッドランナーとして、Ubuntu 26.04（x64/arm64）およびVisual Studio 2026搭載のWindows 11 ARM64イメージがパブリックプレビューとして追加された。"
tags:
  - OSS
references:
  - "https://github.blog/changelog/2026-06-11-new-runner-images-in-public-preview/"
---

## 概要

GitHub Actionsのホステッドランナーに、Ubuntu 26.04（x64・arm64）とWindows 11 ARM64（Visual Studio 2026搭載）の新しいランナーイメージが2026年6月11日よりパブリックプレビューとして追加された。ワークフロー定義に新しいラベルを指定するだけで利用できるため、最新OSへの対応状況を早期に確認したい開発チームはすぐに試せる状態となっている。

## 利用方法と対応イメージ

各イメージの `runs-on` ラベルは以下のとおり。Ubuntu 26.04はx64向けに `ubuntu-26.04`、arm64向けに `ubuntu-26.04-arm` を指定する。基本イメージはラージランナーユーザーも利用可能。Windows 11 ARM64はVisual Studio 2026ツールチェーンを搭載した `windows-11-vs2026-arm` ラベルで利用でき、既存の `windows-11-arm` イメージと並行して稼働する。これにより、既存パイプラインに干渉することなく段階的に新環境への移行や検証を進められる。

## 注意事項と今後の予定

プレビュー期間中はピーク時間帯にキューの遅延が生じる可能性がある点に注意が必要だ。また、Windows 11 ARM64については2026年9月初旬にプレビュー終了を予定しており、その時点で既存の `windows-11-arm` ラベルが新しいVS2026イメージへ移行する。既存のワークフローでこのラベルを使用している場合は、移行後の動作変更を事前に確認しておくことが推奨される。バグ報告やフィードバックはGitHubの `runner-images` リポジトリへ送ることができる。
