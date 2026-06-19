---
date: "2026-06-20T02:41:32+09:00"
title: "DragonForceがMicrosoft Teams TURNリレーを悪用したバックドアでC2通信を隠蔽"
description: "DragonForceランサムウェアグループがGoベースのカスタムバックドア「Backdoor.Turn」を用いてMicrosoft TeamsのTURNリレーインフラを悪用し、C2通信を正規トラフィックに偽装して最長2か月間検知を回避していたことが明らかになった。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/dragonforce-hackers-abuse-microsoft.html"
  - "https://www.securityweek.com/microsoft-teams-relay-servers-abused-in-dragonforce-ransomware-attack/"
  - "https://www.helpnetsecurity.com/2026/06/16/dragonforce-microsoft-teams-malware-backdoor-turn/"
---

## 概要

DragonForceランサムウェアグループが、Microsoft TeamsのTURN（Traversal Using Relays around NAT）リレーインフラを悪用してコマンド＆コントロール（C2）通信を隠蔽する新たな手口を用いていたことが、Symantecの調査によって明らかになった。攻撃者はGoベースのカスタムバックドア「Backdoor.Turn」を展開し、正規のMicrosoftサーバーへのトラフィックとして偽装することで、防御側による検知を1〜2か月にわたって回避した。これはTURNリレーインフラを悪用したマルウェアとして野生環境で初めて確認された事例とされる。標的となったのは米国の大手サービス企業である。

## Backdoor.Turnの技術的仕組み

Backdoor.Turnが採用するC2通信の隠蔽技術は「Ghost Calls」と呼ばれる手法に基づく。具体的には、MicrosoftのSkypeアイデンティティサービスから匿名のTeamsビジタートークンを取得し、正規のMicrosoft TURNリレーサーバーを接続確立に利用したうえで、攻撃者のC2サーバーへのQUICセッションを確立する仕組みだ。ネットワークを監視する防御担当者には正規のMicrosoft Teamsサーバーへの通信しか見えないため、データが外部に持ち出されていることに気付くことが極めて困難となる。

マルウェアの機能は多岐にわたる。コマンド実行・プロセス起動、ネットワークスキャン、TLS証明書情報の取得、LDAP/Active Directoryの列挙、盗んだ認証情報を用いたラテラルムーブメント、ブラウザに保存された認証情報の窃取などが実装されており、ランサムウェア展開後も持続的なアクセス維持のために同バックドアが注入されることが確認されている。研究者たちは「ランサムウェア攻撃者が自前のカスタムツールを使用すること自体が珍しいが、Backdoor.Turnほど洗練されたカスタムツールを使用するのはさらに例外的だ」と指摘している。

## 攻撃のタイムラインと手法

攻撃の初期侵入は2025年12月に遡り、SQL/MSSQLサーバーの脆弱性悪用またはアクセスブローカーの関与が疑われている。侵入後は正規のVirtualBoxやDbgViewをDLLサイドローディングに悪用して追加マルウェアを取得し、偵察活動を開始した。

権限昇格には複数の署名済み脆弱なドライバを持ち込むBYOVD（Bring Your Own Vulnerable Driver）戦略が採用された。悪用されたドライバには、HuaweiのHWAuidoOs2Ec.sys、Topaz AntifraudのCVE-2023-52271（wsftprm.sys）、Tower of FantasyのCVE-2025-61155（GameDriverx64.sys）、K7 SecurityのCVE-2025-1055（K7RKScan.sys）、そしてPalo Alto Networksのドライバを偽装したカスタムドライバ「ABYSSWORKER」が含まれる。セキュリティプロセスを無効化したうえでデータを外部流出させ、最終的にランサムウェアペイロードを展開するまでに1〜2か月の潜伏期間が設けられていた。

## 背景と対応

DragonForceはランサムウェア・アズ・ア・サービス（RaaS）モデルから、高度な標的型攻撃を行う組織的なカルテル構造へと移行しており、今回の攻撃はその継続的な能力開発の一端を示している。Microsoftのクラウドインフラを盾に利用するこの手口は、エンタープライズ環境において広く展開されているコラボレーションツールが新たな攻撃ベクターになり得ることを示す重大な事例だ。Symantecは侵害指標（IoC）を公開しており、セキュリティチームはネットワーク上のTeamsトラフィックの精査と、脆弱なドライバの監視を強化することが求められる。