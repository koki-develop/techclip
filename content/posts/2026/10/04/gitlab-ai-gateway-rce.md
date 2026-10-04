---
date: "2026-10-04T19:56:55+09:00"
title: "GitLabのDuo Agent Platformにサンドボックス脱出の重大な脆弱性、セルフホストでコマンド実行が可能に"
description: "GitLabはDuo Agent PlatformのAI Gatewayに存在するCVSS9.9のテンプレートサンドボックスエスケープ脆弱性(CVE-2026-90970)を修正し、セルフホスト環境の管理者にアップグレードを呼びかけた。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/10/gitlab-patches-critical-self-hosted-ai.html"
  - "https://www.bleepingcomputer.com/news/security/gitlab-warns-of-critical-rce-vulnerability-in-ai-gateway-service/"
  - "https://securityaffairs.com/200283/hacking/cve-2026-90970-critical-gitlab-ai-gateway-flaw-fixed.html"
---

## 概要

GitLabは10月2日、AIコーディング支援機能「Duo Agent Platform」のAI Gatewayに存在する重大な脆弱性(CVE-2026-90970、CVSS9.9)を修正したと発表した。Duo Agent Platformへのアクセス権を持つ認証済みユーザーが、特別に作成したフロー設定を用いてプロンプトテンプレートのサンドボックスを脱出し、AI Gateway上で任意のコマンドを実行できるというものだ。影響を受けるのはセルフホスト環境のAI Gatewayのみで、GitLab.comやGitLab Dedicatedなど、GitLabがホストするゲートウェイを利用するインスタンスは影響を受けない。

## 技術的な詳細

脆弱性はDuo Agent PlatformのカスタムフローにおけるプロンプトテンプレートエンジンのCWE-1336(テンプレートエンジンの不備)に分類される。GitLabの説明によれば、「Duo Agent Platformへのアクセス権を持つ認証済みユーザーが、特定の条件下で特別に作成したフロー設定を介してプロンプトテンプレートのサンドボックスを脱出し、AI Gateway上で任意のコマンド実行につながる可能性があった」という。攻撃には高度な権限は不要で、Duo Agent Platformの基本的な利用権限があれば悪用できる点が特に問題視されている。

なお、このテンプレートエンジン関連の脆弱性クラスは今年2月に修正された別の脆弱性(CVE-2026-1868、同じくCVSS9.9)と同種のものであり、GitLabのAI Gatewayにおいて類似の問題が繰り返し発見されていることになる。

## 影響範囲と修正版

脆弱性は18.1.6以降19.2.3までのバージョン、19.3.0・19.3.1、および19.4.0のAI Gatewayに存在し、それぞれ19.2.4・19.3.2・19.4.1で修正された。該当するのはセルフホストでAI Gatewayを運用している環境のみで、GitLab.comやGitLab Dedicatedなどのクラウド側は既に対応済みのため、利用者側の対応は不要とされている。

コマンド実行に成功した場合、攻撃者はAI Gatewayの基盤インフラへのアクセスを得る可能性がある。同インフラはJSON Web Token(JWT)の署名・検証キーを環境変数として保持し、各種AIモデルプロバイダーとの通信も担っているため、認証情報の窃取や組織内ネットワークへの横展開につながるリスクがある。脆弱性はHackerOne経由でセキュリティ研究者invisiblemeerkatによって報告された。

## 今後の展望

CISAの評価では、2026年10月2日時点で本脆弱性の実際の悪用は確認されておらず、公開された実証コード(PoC)も存在しない。しかし、CVSS9.9という最高レベルの深刻度であることに加え、過去にも同種の脆弱性が発生している経緯を踏まえ、セルフホストでDuo Agent Platformを運用する管理者には速やかなアップグレードが強く推奨される。AIエージェント機能がCI/CDや開発基盤に深く統合される中、プロンプトテンプレートのサンドボックス境界が攻撃対象として注目され続けることになりそうだ。
