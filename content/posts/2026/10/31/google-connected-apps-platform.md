---
date: "2026-10-31T08:07:33+09:00"
title: "Google、サードパーティアプリをGeminiと検索に直接統合する「Connected Apps Platform」を発表"
description: "GoogleがGeminiとGoogle検索にサードパーティアプリを統合できる開発者向けプラットフォーム「Connected Apps Platform」を発表し、Adobeなど既存の50以上のアプリがGeminiで稼働するほか、Calmなどの新規参加も予定されている。"
tags:
  - AI
references:
  - "https://techcrunch.com/2026/10/28/as-ai-agents-reshape-the-web-google-opens-gemini-and-search-to-more-apps"
  - "https://9to5google.com/2026/10/28/gemini-google-connected-apps-platform/"
  - "https://www.androidauthority.com/google-gemini-search-connected-apps-developer-platform-3729015/"
---

## 概要

Googleは10月28日、サードパーティ企業のアプリをGeminiおよびGoogle検索のAI体験に統合できる開発者向けプラットフォーム「Connected Apps Platform」を発表した。これまで外部アプリをGeminiやSearchに連携させるには、Googleとの直接的な協業が必要だったが、今回のプラットフォームによってその敷居が下がり、より多くの開発者が自社サービスをGoogleのAI体験に組み込めるようになる。現時点では米国の開発者向け限定プレビューとして公開されており、Adobe・Experian・Pelotonなど既存のGemini連携アプリがSearchへの対応を広げるほか、新規パートナーとしてCalmが参加した。AIエージェントがウェブの利用形態そのものを変えつつある中、Googleはユーザーがアプリを切り替えずにタスクを完了できる体験を広げることで、サービス発見の主導権をAI側に取り込もうとしている。

## 技術的な仕組みと参加パートナー

開発者は、クラウドホスト型のMCP(Model Context Protocol)サーバー、またはAppFunctions APIを利用したAndroid向けMCPのいずれかの方式でアプリを統合する。登録・テスト・申請は新設された管理画面「Google Connected Console」で行い、公開後はトラフィックや遅延、エラー率といった運用指標を監視できるほか、アプリ内でのブランド表示もコントロールできる。開発者はGeminiとSearchのどちらに対応するか、あるいは両方に対応するかを個別に選択可能だ。すでにGeminiおよびSearchを合わせて50以上の連携アプリが稼働しており、Adobe・Canva・YouTube Music・Peloton・Experian・Localiza・Instacart・Dropbox・OpenTable・Ticketmaster・Yahoo Fantasy Football・Sleeper Fantasy Footballなどが名を連ねる。これらはGoogle Workspace・Google Home・Google Photosといった自社サービスとの連携を補完する形になっている。メディテーションアプリのCalmは、数週間以内にGeminiとSearchの両方で新たに連携を開始する予定だ。

## 今後の展望

Connected AppsはまずGeminiアプリ上での展開が先行してきたが、今後はGoogle検索への拡大も進められる見通しで、開発者はアプリをどのプラットフォームに展開するかを独自に判断できる。プレビューへのアクセスはdevelopers.google.com/connected-appsから申請する形で、今後数カ月かけて段階的に提供範囲を広げ、米国以外の開発者にも対応していく方針だ。Googleとしては、個々のアプリへの直接アクセスからAIを介したサービス利用へと行動が移行する中で、検索エンジン最適化(SEO)に代わる新たな発見経路をいち早く整備し、中小の開発者でも自社サービスをAI体験に組み込める環境を提供することで、エコシステム全体の拡大を狙っている。
