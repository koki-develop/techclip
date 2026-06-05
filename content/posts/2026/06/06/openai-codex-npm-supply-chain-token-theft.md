---
date: "2026-06-06T02:40:25+09:00"
title: "OpenAI Codex装ったnpmパッケージが認証トークンを窃取——週間2.9万DLのサプライチェーン攻撃を解説"
description: "OpenAI Codexの非公式UIを装ったnpmパッケージ「codexui-android」に認証トークン窃取コードが仕込まれ、Aikido Securityの研究者が攻撃を公開した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/openai-codex-authentication-tokens.html"
  - "https://www.techradar.com/pro/security/openai-codex-tool-with-over-29-000-downloads-linked-to-malicious-npm-supply-chain-attack-stealing-authentication-tokens"
  - "https://cybernews.com/security/openai-codex-tool-malware-token-theft/"
---

## 概要

Aikido SecurityのセキュリティリサーチャーCharlie Eriksenが2026年6月1日、OpenAI Codexの非公式リモートWebUIとして広く利用されていたnpmパッケージ「codexui-android」が認証トークンを窃取する悪意あるコードを含んでいることを公開した。同パッケージは週間29,000件以上のダウンロード数を誇り、一見正規のツールとして開発者コミュニティに浸透していた。公開されているGitHubリポジトリのコードは無害であり、npm経由で配布されるビルド成果物にのみ悪意あるコードが混入されるという巧妙な手口が特徴的だ。

## 攻撃の手口と盗まれるデータ

悪意あるコードはバージョン0.1.82以降に含まれるようになり、ローカルの`~/.codex/auth.json`からアクセストークン・リフレッシュトークン・IDトークン・アカウントIDを抜き出す仕組みになっている。窃取された認証情報は、正規のエラー監視サービス「Sentry」を模した偽ドメイン「sentry.anyclaw[.]store」へ送信される。特に危険なのはリフレッシュトークンの扱いで、Eriksenは「リフレッシュトークンには有効期限がない。攻撃者はこれを持つだけで、いつまでも無制限に被害者になりすますことができる」と警告している。窃取されたトークンを悪用すると、Codexのセッションへのアクセス、APIクレジットの不正消費、開発中のプロジェクトやコードの閲覧、OpenAIサービス上での被害者へのなりすましが可能になる。

## Androidアプリへの拡大と攻撃者の同一性

さらにAikido Securityは同一の脅威アクターによる2本のAndroidアプリも発見している。「OpenClaw Codex Claude AI Agent」（50,000件以上のダウンロード）と「Codex application」（10,000件以上のダウンロード）の2本で、いずれも問題のnpmパッケージを内包し、盗んだ認証情報を攻撃者のサーバーに送信していた。Androidアプリがサンドボックス内でNode.jsを実行しnpmパッケージを動かすという構造を悪用しており、モバイルプラットフォームを経由したサプライチェーン攻撃の新たな手口として注目されている。悪意ある通信先ドメインのWHOIS情報によると、当該ドメインはパッケージの初回アップロードからわずか2日後の2026年4月12日に登録されており、攻撃の意図的な計画性がうかがえる。

## 開発者への影響と対応

連絡を受けたパッケージ作者は当初「npmアカウントへのアクセス権を失った」と説明し、後に「社内で調査中」と述べた。しかし第三者との認証情報共有を否定しながら、悪意あるコードが公開GitHubリポジトリではなくnpmビルドにのみ存在する理由や、認証情報へのアクセスが必要な理由については明確な説明がなかった。今回の攻撃はタイポスクワット（よく似た名前の偽パッケージ）ではなく、一定の実績と機能を持つ正規風パッケージを踏み台にする手口であり、AIツール関連のOSSエコシステムを標的にした高度なサプライチェーン攻撃の増加傾向を示している。codexui-androidを利用していた開発者はOpenAIの認証情報を早急にローテーションし、アクティブなセッションを失効させることが推奨される。
