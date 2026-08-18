---
date: "2026-08-19T08:03:44+09:00"
title: "Cursor開発元Anysphere、GitHub対抗のコードホスティング「Origin」をベータ公開"
description: "AIコーディングエディタCursorを手がけるAnysphereが、GitHubに対抗するAIエージェント向けコードホスティング基盤「Origin」の有料ユーザー向けベータを公開した。"
tags:
  - OSS
  - AI
references:
  - "https://techstartups.com/2026/08/17/cursor-launches-origin-a-github-rival-built-for-ai-coding-agents/"
  - "https://finance.biggo.com/news/c7f0fce3-8a85-4da7-92a9-68580d71c7ec"
  - "https://officechai.com/ai/cursor-launches-github-competitor-named-origin/"
---

## 概要

AIコーディングエディタCursorを開発するAnysphereは8月17日、GitHubに対抗するコードホスティング基盤「Origin」の有料ユーザー向けベータを公開した。リポジトリの作成、プルリクエストのレビューやマージ、CI/デプロイ連携までをCursorのインターフェース上に統合し、Vercel・Buildkite・Depotなどのプロバイダとも接続できる。奇しくも同日、GitHubがActionsやプルリクエスト機能に影響する大規模障害を起こしており、フラストレーションを抱えていた開発者の間で一段と注目を集める形となった。

## Originの特徴とGitHubとの違い

Originの設計思想は、既存のGitHub利用を強制的に置き換えるのではなく、段階的な移行を促す点にある。既存のGitHubリポジトリをOriginに同期させつつ、プッシュは引き続きGitHub側にも反映される仕組みを用意し、チームが低コストで試用できるようにしている。もう一つの特徴は、AIエージェントがファイル単位ではなくリポジトリ全体にアクセスできる点だ。Cursorは、AIエージェントがブランチ作成やマルチファイル編集、プルリクエストの発行と反復を人間の開発者よりもはるかに高い頻度でこなす「エージェントスケール」を前提に、Originのインフラを最適化したと説明している。

## SpaceX傘下入り後初の大型プロダクト

Origin公開の背景には、AnysphereをめぐるSpaceXの買収がある。SpaceXは2026年4月に600億ドル評価での独占買収オプションとして100億ドルを支払い、6月16日に全株式交換による買収合意を締結、8月14日に約3億9100万株のSpaceXクラスA株式を発行して買収を完了させた。Originのベータ公開はこのわずか3日後にあたり、SpaceXAI傘下でのAnysphere第一弾の主要プロダクトとなった。買収前のAnysphereはAndreessen Horowitz、Nvidia、Thrive Capitalなどの支援を受け500億ドル超の評価額で資金調達を進めていたとされ、今回の統合によりxAIのメンフィスにある「Colossus」スーパークラスターやGrokのモデル群といった、独立系スタートアップでは得られなかったリソースへのアクセスが可能になるとみられている。

## データ利用をめぐる懸念

一方で、Originの立ち上げにはコードのデータ利用に関する懸念も伴う。企業向けプランでは管理者設定からベータの対象外とすることができるが、個人ユーザーに対するデータ利用ポリシーの詳細は明らかになっていない。SpaceX傘下となったプラットフォームに有料ユーザーのコードが預けられる形となることから、データ管理の透明性を求める声も出ている。GitHub障害との時期の重なりは、記事によれば「製品公開には通常数週間の準備を要する」ことから偶然の可能性が高いとされるが、GitHubは2025年5月から2026年4月の間に257件ものインシデントを起こしており、Actionsの信頼性問題に不満を持つ開発者にとってOriginの登場は象徴的な出来事として受け止められている。
