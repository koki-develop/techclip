---
date: "2026-08-09T20:06:54+09:00"
title: "Microsoft月例パッチでCVSS10.0の脆弱性3件、Appleは認証不要のScreen Sharing RCEを修正"
description: "Microsoftが8月の月例更新でTeamsやAzure、Entraなどにまたがる深刻な脆弱性を修正し、Appleも認証不要でroot権限奪取が可能なmacOS Screen Sharingの脆弱性にパッチを適用した。"
tags:
  - Security
references:
  - "https://www.securityweek.com/microsoft-apple-release-fresh-security-updates/"
  - "https://www.huntress.com/blog/macos-screen-sharing-rce-patched"
---

## 概要

Microsoftは8月6日、Active Directory、Azure、Entra、SharePoint、Teamsなど複数製品にまたがる12件以上の脆弱性を修正する月例セキュリティアップデートを公開した。うち3件はCVSSスコアが最大値の10.0/10で、いずれもネットワーク経由で悪用可能な深刻な欠陥だった。同日、AppleもmacOSのScreen Sharing機能に存在する認証バイパスの脆弱性(CVE-2026-65400)を修正しており、悪用されれば認証情報なしにroot権限でのリモートコード実行につながる恐れがあったとセキュリティ企業Huntressが指摘している。

## Microsoftの深刻な脆弱性

CVSS 10.0を記録した3件は、Planetary Computer Proの認証欠如(CVE-2026-63508)、Azure SQLデータベースの認証不正(CVE-2026-56162)、Teamsの認可欠如(CVE-2026-65667)。いずれも特権昇格やリモートコード実行につながる可能性があり、攻撃者による悪用の前提条件が低いとされる。これに次いでCVSS 9.9を記録した4件には、Azure Service Busのリモートコード実行(CVE-2026-50515)、Azure SREエージェントの特権昇格(CVE-2026-62830)、Entraプロビジョニングサービスの特権昇格(CVE-2026-59115)、Active Directoryの特権昇格(CVE-2026-50481)が含まれる。影響範囲はAzure、Entra、SharePoint、Teams、Office 365など企業の基幹インフラに広く及んでおり、管理者には速やかな適用が推奨されている。

## AppleのScreen Sharing脆弱性

Appleが修正したCVE-2026-65400は、Screen Sharingの認証プロトコルであるSecure Remote Password(SRP)の実装不備に起因する。`screensharingd`のSRP処理においてフレーム長の検証に誤りがあり、本来失敗すべき認証が誤って成功状態を返してしまう。これにより暗号保護のないクリアテキストのセッションが確立され、Appleの署名付きエンタイトルメント「kTCCServiceSystemPolicyAllFiles」を持つ`SSFileCopySender`を通じて、攻撃者は完全ディスクアクセスを取得できてしまう。任意のファイルシステムアーティファクトの読み書きが可能になるため、LaunchDaemonの作成やシェル起動ファイルの改ざんによってroot権限でのリモートコード実行に発展しうる。

Huntressはこの脆弱性と合わせて、認証が必要な別の脆弱性CVE-2026-43760(bynar.ioが7月29日に公開)も分析している。こちらはレガシーVNC認証を通過したユーザーが「confused-context」条件を悪用し、root権限でファイルシステムを操作できるというもので、CVE-2026-65400ほど深刻ではないものの、同じScreen Sharing機能の設計上の弱点を突くものだ。

## 影響範囲と対策

CVE-2026-65400の影響を受けるのはmacOS Tahoe(26)26.6以前、Sequoia(15)15.7.8以前、Sonoma(14)14.8.8以前で、Appleは8月6日にそれぞれ26.6.1、15.7.9、14.8.9で修正した。特にホスティングされたベアメタルAppleデバイスサービス(Mac miniなど)ではScreen Sharingがデフォルトで有効化されインターネットに露出しているケースがあり、Censysのスキャンでは数万台規模の潜在的に脆弱なホストが確認されているという。Huntressは、許可ユーザーの削除やVNC認証の無効化といった通常の対策はこの認証前の脆弱性には効果がないとし、Endpoint Securityフレームワークを用いた`ES_EVENT_TYPE_NOTIFY_SCREENSHARING_ATTACH`イベントの監視(暗号化なしのSRP認証やroot権限セッションの検知)や、速やかなOSアップデートの適用を推奨している。
