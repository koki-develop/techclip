---
date: "2026-07-04T02:33:35+09:00"
title: "GitHub CopilotがブラウザツールとVision機能をGA、初のオープンウェイトモデルKimi K2.7 Codeも追加"
description: "GitHub Copilotが7月1日に複数機能を一斉GA提供し、ブラウザ自動操作・画像PDFの視覚認識・オープンウェイトモデルKimi K2.7 Codeをすべてのプランで利用可能にした。"
tags:
  - OSS
  - AI
references:
  - "https://github.blog/changelog/2026-07-01-browser-tools-for-github-copilot-in-vs-code-are-generally-available/"
  - "https://github.blog/changelog/2026-07-01-copilot-vision-is-generally-available/"
  - "https://github.blog/changelog/2026-07-01-kimi-k2-7-is-now-available-in-github-copilot/"
---

## 概要

GitHubは2026年7月1日、GitHub Copilotに関する複数の機能強化を一斉に一般提供（GA）開始した。VS Code向けのブラウザツール、画像・PDFを扱えるCopilot Vision、そしてCopilot初のオープンウェイトモデルであるKimi K2.7 Codeの3本立てで、開発者のAI支援体験を大きく広げる内容となっている。

## ブラウザツール：エージェントによる実ブラウザ操作

VS Code向けブラウザツールのGAにより、GitHub CopilotのAIエージェントが実際のブラウザを直接操作できるようになった。クリック・入力・ホバー・ドラッグ・ダイアログ処理といった操作を実行し、ページコンテンツの読み取りやコンソールエラーの取得、スクリーンショット撮影も可能だ。エージェントがWebアプリを自律的に検証し、その結果をチャットにフィードバックするという使い方が想定されている。

プライバシー保護の観点から、ユーザーが開いているページはエージェントが「Share with Agent」を明示的に選択しない限りアクセスできない設計になっている。またエージェント用タブはクッキーやストレージへのアクセスが遮断されており、カメラ・マイク・位置情報などの権限は自動承認されない。企業向けには管理者が`workbench.browser.enableChatTools`でオンオフを制御でき、`chat.agent.allowedNetworkDomains`や`chat.agent.deniedNetworkDomains`によるドメイン単位の通信制限も利用できる。

## Copilot Vision：画像・PDFの視覚的推論

Copilot VisionのGAにより、チャットプロンプトにJPEG・PNG・GIF・WebP形式の画像およびPDFを直接添付して、Copilotに視覚的なコンテキストを与えることができるようになった。VS Code（貼り付け・ドラッグ＆ドロップ・右クリック）、github.com上のCopilot Chat、GitHub Copilot CLIの3環境で利用可能だ。

今回のGAでは、Free・Pro・Pro+・Business・Enterpriseのすべてのプランが対象となった。以前はBusinessとEnterpriseユーザーがEditor Preview Featuresポリシーを手動で有効化する必要があったが、現在はデフォルトで全員が使える。BusinessおよびEnterpriseユーザーの添付ファイルはGitHubが約24時間保持するデータ保持ポリシーが適用される。

## Kimi K2.7 Code：Copilot初のオープンウェイトモデル

Kimi K2.7 CodeはCopilotのモデルピッカーに加わった初のオープンウェイトモデルで、Microsoft Azure上でGitHubがホストしている。利用料金はプロバイダーのリスト価格に基づく使用量課金となる。

ロールアウトはCopilot Pro・Pro+・Maxプランから順次開始しており、BusinessおよびEnterpriseへの展開は数週間後を予定している。対応環境はVS Code（1.127.0以降）・Visual Studio（17.14.6以降）・Copilot CLI・JetBrains・Xcode・Eclipseと幅広い。なおBusinessおよびEnterpriseでは初期設定でオフになっており、管理者がCopilot設定からポリシーを有効化したうえで組織のセキュリティ要件を確認することが推奨されている。

## まとめ

ブラウザ操作・画像理解・オープンウェイトモデルという3機能のGA同時リリースは、GitHub CopilotをIDEの補完ツールからエージェントプラットフォームへと進化させる方向性を示している。特にブラウザツールはフロントエンド開発やQAフローへの直接統合を可能にし、Copilot Visionはデザイン仕様や図面をそのままAIに渡せる実用性を提供する。Kimi K2.7 Codeの追加によりオープンウェイトモデルの選択肢も広がり、コスト管理や透明性を重視する企業ユーザーにとっても選択の幅が広がった。
