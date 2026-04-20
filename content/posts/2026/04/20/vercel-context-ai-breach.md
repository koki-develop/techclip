---
date: "2026-04-20T18:33:14+09:00"
title: "VercelがContext.ai経由のサプライチェーン侵害を公表、顧客APIキー・環境変数に漏洩の可能性"
description: "VercelはサードパーティAIツール「Context.ai」の侵害を起点としたサプライチェーン攻撃により、一部顧客のAPIキーや環境変数が漏洩した可能性があることを公表した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/vercel-confirms-breach-as-hackers-claim-to-be-selling-stolen-data/"
  - "https://thehackernews.com/2026/04/vercel-breach-tied-to-context-ai-hack.html"
  - "https://cybersecuritynews.com/vercel-data-breach/"
---

## 概要

クラウド開発プラットフォームのVercelは2026年4月、サードパーティAIツール「Context.ai」の侵害を経由した内部システムへの不正アクセスを確認したと発表した。Vercel CEO の Guillermo Rauch 氏によると、攻撃者はまずContext.aiの従業員を侵害し、そこから取得したGoogle Workspaceの認証情報を使ってVercel環境へのアクセスを拡大したという。影響を受けたのは「顧客の限定的なサブセット」にとどまるとされているが、APIキーや環境変数の漏洩が確認されており、影響を受けた顧客には直接通知と認証情報のローテーションが要請されている。

## 攻撃の経路：サプライチェーン経由の侵害

セキュリティ企業Hudson Rockの調査によると、攻撃の起点は2026年2月に遡る。Context.aiの従業員がRobloxのゲームチートツール（「自動農業」スクリプトやエクスプロイト）をダウンロードしたことで、それらに組み込まれていた「Lumma Stealer」と呼ばれる情報窃取型マルウェアに感染した。このマルウェアを通じて攻撃者はGoogle Workspaceの認証情報や、Supabase・Datadog・Authkitなどのサービスキーを入手した。さらに「support@context.ai」アカウントを奪取することでVercelのシステムへの権限昇格を実現した。調査チームは、攻撃者がVercelのシステム構造を深く理解していた点から、高度に洗練された脅威グループと評価している。

## 漏洩データの範囲とVercelの対応

脅威行為者が主張する漏洩データには、従業員情報580件（名前・メールアドレス・アカウントステータス・アクティビティタイムスタンプ）、NPMトークンおよびGitHubトークンを含むAPIキー、ソースコード、内部デプロイメントへのアクセス権が含まれるとされる。ただし「Sensitive（機密）」としてマーク済みの環境変数は暗号化されており、現時点でアクセスされた証拠はないとVercelは説明している。「ShinyHunters」と名乗る脅威行為者がBreachForumsでデータを約200万ドルで売り出していると報告されているが、BleepingComputerはデータの真正性を独自に確認できていない。

Vercelは対応策として、Mandiant（Google傘下）をはじめとする複数のサイバーセキュリティ企業と連携し、法執行機関への通知も完了させている。また、全ユーザーに対して環境変数の監査と「Sensitive（機密）」設定の活用、シークレットのローテーションを推奨している。なお、Next.js・Turbopackなどのオープンソースプロジェクトは本インシデントの影響を受けていないことが確認されている。

## サードパーティツール利用リスクへの教訓

今回のインシデントは、従業員が利用するサードパーティSaaSやAIツールが企業全体のセキュリティチェーンにおける脆弱点になり得ることを改めて示した。攻撃者は直接Vercelを攻撃するのではなく、権限を持つ従業員が利用するツールのベンダーを狙うことで、多要素認証などの直接的な防御策を迂回した。企業はサードパーティツールへのアクセス権限の最小化、OAuthアプリケーションIDの定期的な監視、シークレット情報の暗号化管理の徹底など、サプライチェーンリスクへの対策を強化する必要がある。
