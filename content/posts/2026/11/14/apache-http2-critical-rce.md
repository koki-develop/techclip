---
date: "2026-11-14T18:07:47+09:00"
title: "Apache HTTP ServerにCVSS 9.8の未認証RCE脆弱性、AnthropicとGoogleが発見しv2.4.71で修正"
description: "Apache HTTP Serverのmod_http2に未認証の攻撃者がリモートでコードを実行できる重大なレース条件の脆弱性(CVE-2026-119618)が見つかり、修正版2.4.71がリリースされた。"
tags:
  - Security
references:
  - "https://www.securityweek.com/apache-patches-critical-http-server-rce-found-by-anthropic-google/"
  - "https://www.bleepingcomputer.com/news/security/apache-http-server-patches-critical-http-2-remote-code-execution-flaw/"
  - "https://thehackernews.com/2026/11/critical-apache-http2-flaw-could-let.html"
---

## 概要

Apache HTTP Serverの開発チームは11月11日、HTTP/2モジュール「mod_http2」に存在する重大な脆弱性(CVE-2026-119618、CVSS 9.8)を修正したバージョン2.4.71をリリースした。この脆弱性は、複数スレッドが共有リソースに不適切にアクセスすることで発生するレース条件(Concurrent Execution using Shared Resource with Improper Synchronization)であり、`assign_headers()`関数におけるヒープメモリの破損を通じて、未認証の攻撃者がサーバープロセスの権限でリモートからコードを実行できる可能性がある。攻撃にはネットワーク経由でサーバーに到達できること以外の条件は不要で、認証は一切求められない。

影響を受けるのはApache HTTP Server 2.4.55から2.4.70までのバージョンで、HTTP/2が有効になっている構成に限られる。HTTP/2は多くのディストリビューションでデフォルト無効となっているため、HTTP/1.1のみで運用している環境は影響を受けない。また、mod_http2から分岐したスタンドアロンのmod_h2プロジェクト(バージョン2.0.8～2.0.42)も同様に脆弱だが、このリポジトリは既にアーカイブされており、修正版は提供されない見通しだ。

## 発見の経緯と実際の脅威度

この脆弱性は、Anthropicの自動化されたOSSスキャナーが10月26日に報告したのを皮切りに、Google CloudのAnthony WeemsとSimon Scannellが11月3日に独立して報告したことで、AI企業発の脆弱性発見として注目を集めている。セキュリティ企業Wizの分析によれば、報告時点で公開された攻撃コードは存在せず、実環境での悪用も確認されていなかった一方、ベンダー側の評価では「信頼性の高いエクスプロイトの実証が公開研究によって示されている」との記述もあり、情報源間で実証状況の捉え方にはやや幅がある。実際に公開されている検証コードは、メモリ破損とプロセスクラッシュまでの再現に留まり、リモートコード実行そのものの実証には至っていないとされる。

Wizのテレメトリ分析では、クラウド環境の64%が脆弱なApacheのバージョンを含んでおり、そのうち約半数が外部に公開されたインスタンスを運用しているという。ただし個々のサーバー設定(HTTP/2の有効化状況など)までは反映されていない数値であり、実際に攻撃可能な対象の規模はこれより小さいとみられる。Red Hat Enterprise Linux 9/10向けにはそれぞれRHSA-2026:98981、RHSA-2026:98978として個別のパッチが提供されており、Red HatはHTTP/2ストリームごとに別個のメモリアロケータを用いる自社実装により「攻撃の難易度が大幅に高まる」としている。

## 対応策

管理者には、まずApache HTTP Server 2.4.71への早急なアップグレードが推奨される。すぐに更新できない環境向けの緊急対応としては、設定ファイルの`Protocols`ディレクティブから`h2`および`h2c`を除外し、`Protocols http/1.1`のみを残すことでHTTP/2を無効化する回避策が案内されている。スタンドアロン版のmod_h2を利用している利用者は、プロジェクト自体がアーカイブされ修正版が出ない以上、この回避策が実質的に唯一の防御手段となる点に注意が必要だ。CVSS 9.8という最高レベルに近い深刻度と、クラウド環境における広範な分布を踏まえると、公開エクスプロイトが出現する前にパッチ適用を完了させることが望ましい。
