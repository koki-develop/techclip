---
date: "2026-11-22T18:08:34+09:00"
title: "Atlassian、2026年11月のセキュリティ更新で318件の脆弱性を修正 LodashやSpring由来のRCEなど重大度52件を含む"
description: "AtlassianがJira・Confluence・Bitbucket・Bamboo・Crowdなど主要製品を対象に2026年11月のセキュリティ更新を公開し、サードパーティ依存ライブラリ起因の脆弱性を含む計318件を修正した。"
tags:
  - Security
references:
  - "https://gbhackers.com/atlassian-releases-november-2026-security-updates/"
  - "https://cybersecuritynews.com/atlassian-patches-318-security-vulnerabilities/"
  - "https://cyberpress.org/atlassian-patches-318-security-vulnerabilities/"
---

## 概要

Atlassianは11月17日、Jira Software、Jira Service Management、Confluence、Bitbucket、Bamboo、Crowd、Fisheye、Crucibleなど主要製品を対象とした2026年11月のセキュリティ更新を公開した。修正された脆弱性は計318件に上り、重大度「高」が266件、「重大(Critical)」が52件を占める。10月の更新が176件だったのに対し大幅に増加しており、エンタープライズ向け製品群における継続的なセキュリティメンテナンスの規模を示す結果となった。なお同一のCVEが複数製品にまたがって計上されているケースもあり、318件という数字がそのまま318種類の異なる欠陥を意味するわけではないとAtlassianは注記している。

## 重大な脆弱性の詳細

今回の更新で特に注目されるのは、サードパーティライブラリに起因する重大(Critical)評価の欠陥群だ。Confluence Data CenterではLodashライブラリに起因する遠隔コード実行の欠陥(CVE-2026-4800、CVSS 9.8)が修正され、同じくConfluence Data Centerではファイルを意図したディレクトリ外で読み書きできるパストラバーサルの欠陥(CVE-2026-21605、CVSS 8.7)も対応された。BambooおよびCrowdではSpring Frameworkに起因する遠隔コード実行の欠陥(CVE-2026-47890、CVSS 9.8)が、Bitbucket/Bambooでは侵害されたeMudhra証明書を含むDockerイメージの暗号問題(CVE-2026-91403、CVSS 9.1)が報告されている。Bitbucketでは、Jackson Databindの安全でないデシリアライゼーションに起因する欠陥(CVE-2026-54513、CVSS 8.1)も含まれる。これらに加え、ストアド型クロスサイトスクリプティング、サービス拒否、OSコマンドインジェクション、HTTPリクエストスマグリング、認証・セッション管理の不備など、幅広い脆弱性クラスが今回の修正対象に含まれている。

## サードパーティ依存ライブラリの問題

今回の更新で目立つのは、Atlassian自身のアプリケーションコードではなく、Tomcat、Spring、Bouncy Castle、Eclipse Jetty、Nettyといったバンドルされたサードパーティコンポーネントに起因する欠陥が多数を占めている点だ。Lodashに起因するCVE-2026-4800のような深刻度9.8の欠陥も、実際の製品実装における悪用可能性は個別に評価する必要があるとAtlassianは説明しており、CVSSスコアが高いことが必ずしも実運用環境における即時のリスクを意味しない点に注意を促している。一方で、こうした依存ライブラリの脆弱性は複数製品に同時に影響するため、Jira・Confluence・Bitbucketなど複数のAtlassian製品を併用する組織では、各製品の個別アドバイザリを横断的に確認し、バージョンの整合性を取る作業が必要になる。

## 対応と今後の見通し

Atlassianは、重大なリスクを伴う欠陥については今回の一括バルletinに加えて個別のCritical Security Advisoryを発行する方針を示しており、管理者は両方を継続的に監視する必要がある。特にBamboo Data CenterのようにサーバーエディションやLTS(長期サポート)リリースを利用している組織は、推奨バージョン(例:Bamboo Data Center R12.1.13など)への更新を優先的に検討すべきとされる。今回の更新は、クラウド基盤の普及が進む中でも自己管理型(Server/Data Center)製品が依然として広く使われている実態を改めて示しており、サードパーティ依存関係の継続的な棚卸しとパッチ適用体制の整備が、エンタープライズ製品を運用する組織にとって重要な課題であることを浮き彫りにしている。
