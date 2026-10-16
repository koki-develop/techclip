---
date: "2026-10-16T18:13:52+09:00"
title: "SAP、Cloud SDK for PythonにCVSS最大値10.0のOAuth2認証情報窃取バグ、2026年3月から存在"
description: "SAPがCloud SDK for Pythonのtenant_subdomainパラメータを悪用したOAuth2 SSRF脆弱性(CVE-2026-89111、CVSS 10.0)を公開し、NetWeaverやS/4HANAの他の重大な欠陥とともにパッチを提供した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/sap-warns-of-maximum-severity-oauth2-ssrf-security-flaw/"
  - "https://thehackernews.com/2026/10/sap-discloses-critical-cvss-10-flaw-in.html"
  - "https://www.securityweek.com/sap-patches-critical-netweaver-s-4hana-vulnerabilities/"
---

## 概要

SAPは10月14日のセキュリティパッチデーで22件のセキュリティノートを公開し、そのうちCloud SDK for PythonのOAuth2 SSRF脆弱性(CVE-2026-89111)にCVSS最大値の10.0を付けた。この欠陥は、SAP Business Technology Platform(BTP)上で動くマルチテナントアプリケーションが外部から受け取るtenant_subdomainパラメータを検証せずにOAuth2トークンリクエストのURL構築に使っていたことが原因で、攻撃者が任意の値を渡すことでトークンリクエストを自分が管理するサーバーへリダイレクトさせ、アプリケーションのクライアントIDとクライアントシークレットを窃取できるというものだった。認証不要かつリモートから攻撃可能で、GitHubユーザーのSunandMが報告したとされ、現時点で実際の悪用は確認されていない。

## 脆弱性の技術的背景

SAP Cloud SDK for Pythonは2026年3月16日のPyPI初回リリース時点からこの欠陥を抱えていた。SAPは8月21日リリースのバージョン0.45.2で検証処理を追加して一度は対処したが、9月10日から18日にかけて配布されたバージョン0.53.0〜0.55.0ではDestinationサービスモジュールにこの検証が欠落し、脆弱性が再発(リグレッション)していた。9月18日のバージョン0.55.1で全モジュールへの検証が復元され、最終的に10月13日に公開のセキュリティアドバイザリとして開示された。現在の最新版は0.58.4で、0.45.2〜0.52.2および0.55.1〜0.58.4が安全なバージョンとされる。アドバイザリでは、URL区切り文字を含むtenant_subdomainを渡すと直ちにValueErrorが発生し、認証情報が攻撃者の管理するエンドポイントへ静かに送られる事態を防ぐようになったと説明されている。パッチ適用が困難な組織に対しては、SDK呼び出し前にtenant_subdomainを登録済みテナントのアローリストと照合して検証するよう、SAPは暫定的な緩和策を提示している。

## 同時に修正された他の重大な脆弱性

今回のパッチデーでは、OAuth2の欠陥以外にも複数の重大な脆弱性が修正された。NetWeaver Visual Composerのポータル機能にはアクセス制御の不備(CVE-2026-89110、CVSS 9.9)があり、低権限の攻撃者が事前設定済みの遠隔システム上で内部操作を呼び出し、システムを完全に乗っ取れる可能性があった。S/4HANAのルール定義処理には入力検証不足によるコードインジェクションの欠陥(CVE-2026-89107、CVSS 9.9)があり、特定のFioriアプリケーションのビジネスロールを持つ認証済み攻撃者が任意のABAPコードを実行できた。また、Manufacturing Integration and Intelligenceでは権限確認の欠落(CVE-2026-89108、CVSS 9.1)により、XMII Admin権限を持つユーザーが管理者アカウントを新規作成し、システムを完全に制圧できる状態だった。これらに加えてCommerce Cloud、NetWeaver、ABAP Platformに対してSQLインジェクションやプロセスクラッシュ、制限回避などの高severity脆弱性も修正されている。

## 影響と展望

SAPは全世界の上位100社のうち99社で利用されており、米CISA(サイバーセキュリティ・インフラセキュリティ庁)は2021年11月以降、実際に悪用が確認されたSAP関連の脆弱性を14件カタログ化しており、そのうち3件はランサムウェア攻撃にも関与していた。今回公開された欠陥群は現時点で悪用は報告されていないものの、CVSS 9以上の重大な脆弱性が複数同時に公開されたことから、SAPは対象顧客に対して速やかなパッチ適用を強く推奨している。特にマルチテナントBTPアプリケーションを運用する組織は、OAuth2 SSRFの影響範囲が認証情報の窃取に直結する点を踏まえ、SDKの更新と暫定的なアローリスト対策の双方を優先的に検討すべき状況にある。
