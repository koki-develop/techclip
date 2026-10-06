---
date: "2026-10-07T08:12:33+09:00"
title: "Atlassian製品群に未認証ファイル読み取りの重大脆弱性、Jira・Confluenceなど8製品が対象"
description: "AtlassianがJira・Confluence・Bitbucketなど自社ホスト型8製品に影響するCVSS9.3のパストラバーサル脆弱性(CVE-2026-21589)を公開し、管理者に直ちのパッチ適用を促した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/atlassian-warns-of-critical-file-access-flaw-in-jira-confluence/"
  - "https://thehackernews.com/2026/10/critical-atlassian-flaw-lets.html"
  - "https://www.helpnetsecurity.com/2026/10/06/atlassian-data-center-cve-2026-21589/"
---

## 概要

Atlassianは10月5日、自社ホスト型のJira、Confluence、Bitbucketなど8つのData Center製品に影響する重大な脆弱性(CVE-2026-21589)を公表した。CVSS v4.0で9.3という高いスコアが付けられており、未認証の攻撃者がネットワーク経由でWebアプリケーションルートディレクトリ内の特定ファイルを読み取れる、パストラバーサル型の脆弱性だ。悪用には対象ファイルの正確な名前とパスを事前に知っている必要があり、ディレクトリの列挙自体はできないとAtlassianは説明している。クラウド版は既にパッチが適用済みで対応は不要だが、セルフホスト版を運用する管理者には直ちのアップグレードが強く推奨されている。

## 影響範囲と修正版

対象となるのはBitbucket Data Center、Confluence Data Center、Jira Software/Jira Service Management Data Center、Bamboo Data Center、Crowd Data Center、Crucible、Fisheyeの8製品。修正版はそれぞれBitbucketが9.4.26・10.2.8・10.5.1、Confluenceが9.2.26・10.2.19、Jira Software/Service Managementが9.12.40(Service Managementは5.12.40)・10.3.26・11.3.12、Bambooが10.2.24・12.1.12、Crowdが6.3.7・7.0.3・7.1.7・7.2.4、Crucible/Fisheyeが4.9.15となっている。CVSSの評価では、攻撃元区分がネットワークで認証や利用者の操作を必要としない一方、機密性への影響は高いものの、完全性・可用性への影響は脆弱性のあるシステム自体には及ばないとされる。ただし、読み取られたファイルの内容次第で連携する他システムが危険にさらされる可能性がある。なおBitbucket Cloudはこの脆弱性の影響を受けず、Atlassianはクラウド基盤を調査した結果、現時点で悪用の証拠は見つかっていないと報告している。

## 一時的な緩和策と検知方法

即時のパッチ適用が難しい組織向けに、Atlassianは3つの一時的な緩和策を提示している。1つはWAFやリバースプロキシで、スラッシュ・バックスラッシュ・コロン二重表記(URLエンコードされたものを含む)に隣接する「..」を含むURLをブロックするルール。2つ目はConfluence、Jira Software、Jira Service Management、Bamboo、Crowd向けのTomcat RewriteValve設定、3つ目はBitbucket向けのurlrewrite.xmlによるURL書き換えルールだ。CrucibleとFisheyeはWAFによる対策のみに対応する。すでに侵害を受けていないか確認するため、アクセスログ上でURLデコードされた「..」とパス区切り文字の組み合わせを探すことが推奨されており、リクエスト行を最大2回URLデコードしてパターンを検索する方法と、Atlassianが示すブロックパターンを生ログに直接適用する方法の2つの検知手法が案内されている。

## 過去の類似事例と今後の展望

この脆弱性は、Jira ServerおよびData Centerにおける特定ファイルの読み取りを可能にした過去のパストラバーサル脆弱性CVE-2021-26086と類似する構造を持つ。CVE-2021-26086は米CISAが2024年11月12日付で既知の悪用済み脆弱性(KEV)として指定した経緯があり、同種の脆弱性が長期間にわたり攻撃者に狙われ続けるリスクを示している。今回のCVE-2026-21589についても現時点で悪用は確認されていないものの、ファイルパスの事前知識さえあれば認証不要で攻撃が成立する手軽さから、公開情報をもとにした攻撃コードの出現が懸念される。Atlassian製品をセルフホストする組織は、パッチ適用を最優先としつつ、適用までの期間は提示された緩和策とログ監視を組み合わせて対応することが求められる。
