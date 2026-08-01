---
date: "2026-08-02T08:16:40+09:00"
title: "TeamCityに認証不要のRCE脆弱性、CVSS 9.8のCVE-2026-63077をJetBrainsが公表"
description: "JetBrainsはオンプレミス版TeamCityのエージェントポーリングプロトコルに存在する認証バイパス脆弱性(CVE-2026-63077、CVSS 9.8)を公表し、修正版への更新を強く呼びかけている。"
tags:
  - Security
  - OSS
references:
  - "https://www.bleepingcomputer.com/news/security/jetbrains-warns-of-critical-teamcity-remote-code-execution-flaw/"
  - "https://thehackernews.com/2026/07/critical-teamcity-flaw-could-let.html"
  - "https://www.helpnetsecurity.com/2026/07/28/teamcity-rce-cve-2026-63077-fixed/"
---

## 概要

JetBrainsは、CI/CDツール「TeamCity」のオンプレミス版全バージョンに存在する深刻な脆弱性CVE-2026-63077を公表した。CVSSスコアは最大値に近い9.8(Critical)で、未認証の攻撃者がHTTP(S)でTeamCityサーバーにアクセスできれば、ログイン情報なしにTeamCityサーバープロセスの権限で任意のOSコマンドを実行できてしまう。悪用された場合、TeamCityのデータや設定、保存済み認証情報が露出するほか、ビルド成果物やCI/CDパイプライン自体が改ざん・侵害される恐れがある。JetBrainsは本脆弱性の悪用は現時点で確認されていないとしているが、TeamCityは過去にも国家支援型の攻撃グループやランサムウェア関連組織に狙われた実績があり、迅速な対応が求められる。

## 技術的な詳細

脆弱性の核心は、TeamCityのビルドエージェントとサーバー間の通信に使われる「エージェントポーリングプロトコル」にある。このプロトコルの実装不備を突くことで、攻撃者は通常必要な認証チェックを回避し、サーバー側でOSコマンドを実行できてしまう。ログイン画面を経由する必要がないため、攻撃のハードルは非常に低い。本脆弱性はセキュリティ研究者のAntoni Tremblay氏が2026年7月10日に非公開でJetBrainsに報告し、JetBrains側は同月27〜28日にかけて修正版と共に勧告を公開した。

## 対象範囲と対応状況

影響を受けるのはTeamCity On-Premises(オンプレミス版)の全バージョンで、クラウド版のTeamCity Cloudは既に対策が適用済みのためユーザー側の対応は不要とされている。JetBrainsはオンプレミス利用者に対し、バージョン2025.11.7または2026.1.3への更新を強く推奨している。すぐにアップグレードできない環境向けには、2017.1以降の古いバージョンにも適用可能なセキュリティパッチプラグインが提供されている。

## 追加の緩和策

恒久的な修正の適用に加え、JetBrainsはネットワークレベルでの防御も推奨している。具体的には、インターネットに公開されたサーバーへのアクセスはVPN経由に限定すること、ログイン画面やREST APIをインターネットに直接露出させないこと、そしてTeamCityを必要最小限のOS権限で実行することを挙げている。TeamCityは過去にも深刻な脆弱性が実際の攻撃キャンペーンで悪用された経緯があるため、パッチ適用とあわせてこうした多層的な防御策の実施が望まれる。
