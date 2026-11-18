---
date: "2026-11-19T08:07:31+09:00"
title: "Microsoft公式PyPIパッケージ「agent-framework」が改ざん、認証情報窃取マルウェアが混入"
description: "MicrosoftのAIエージェント開発用パッケージ「agent-framework」の2バージョンがPyPI上で改ざんされ、Python起動時に自動実行される認証情報窃取マルウェアが混入していたことが判明した。"
tags:
  - Security
  - AI
references:
  - "https://www.bleepingcomputer.com/news/security/microsofts-agent-framework-pypi-package-compromised-to-steal-credentials/"
  - "https://thehackernews.com/2026/11/attackers-compromise-microsofts-agent.html"
  - "https://www.theregister.com/security/2026/11/18/microsofts-official-python-agent-framework-hijacked-to-distribute-malware/5310858"
---

## 概要

Microsoftが提供するAIエージェント開発用Pythonパッケージ「agent-framework」が、PyPI上で改ざんされ、認証情報を窃取するマルウェアが混入していたことが判明した。影響を受けたのはバージョン1.26.1と1.26.2で、いずれも11月17日にPyPIへ公開された。同パッケージは月間約19万〜20万件のダウンロードがある主要パッケージで、1.26.1の公開から約33分後に1.26.2が公開され、検出・隔離までにそれぞれわずか数分というスピードで対応が行われた。安全なバージョンは1.26.0で、現在両方の不正バージョンはPyPI側で隔離（quarantine）済みとなっている。

攻撃者がどのようにして配布権限を得たかについて、報道内容には食い違いが見られる。BleepingComputerとThe Hacker Newsは侵入経路が不明としているのに対し、The Registerは「Microsoftが所有するGitHub organizationの管理者権限が不正に入手され、それを足がかりにPyPIへの不正アップロードが行われた」と報じている。

## マルウェアの手口と窃取対象

混入したマルウェアは、`.pth`ファイルという仕組みを悪用して仕込まれていた。`.pth`ファイルはPythonインタプリタの起動時に自動的に読み込まれるため、該当パッケージを明示的にインポートしなくても、Pythonを起動するだけでマルウェアが実行される。バージョン1.26.1では`agent_framework_meta.pth`、1.26.2では`af_runtime_diag.pth`という名前のファイルが使われ、裏では正規の`agent-framework-core` 1.26.0の依存関係も通常通り動作するため、利用者が異変に気づきにくい巧妙な作りになっていた。

窃取対象は広範にわたる。Azureのマネージドアイデンティティ・アクセストークン、Azure DevOpsのOIDCトークン、GitHub ActionsのOIDCトークン（1.26.2のみ）に加え、`~/.azure/*.json`、`.npmrc`、`pip.conf`、`.netrc`、`.git-credentials`、Dockerの設定ファイル、Hugging Faceのトークン、AWSやOpenAIの認証情報など、開発環境に存在する幅広い機密情報が対象となった。The Hacker Newsによれば、Azureのインスタンスメタデータも最大8,000文字分取得される仕組みがあったという。窃取したデータはzlib圧縮・Base64エンコードされたうえで、HTTPS POSTによりwebhook.site上の攻撃者管理下のエンドポイント（`webhook[.]site/d381fd80-ec62-42ad-8f5c-d1b15103c9bb`）へ送信された。マルウェア自体に永続化機能はなく、不正バージョンがインストールされている間だけ動作する。

## 発見の経緯とMicrosoftの対応

この改ざんは、Socket、StepSecurity、OX Security、Aikido、Chainguard、Endor Labs、SafeDep、Wiz、OpenSourceMalwareなど、複数のセキュリティ企業・研究者が独立して検出・報告した。発見・報告は11月17日夜から18日朝（UTC)にかけて相次ぎ、PyPI側も短時間で両バージョンを隔離している。

Microsoftは調査の一環としてagent-frameworkのリポジトリを非公開化した。これと同時期にONNX Runtimeのリポジトリもオフラインになっていることが指摘されているが、The Registerによれば、Microsoftも研究者もこのONNX Runtimeのリポジトリ非公開化とagent-frameworkのマルウェア事件との関連は確認していない。同社は「不正なコンテンツを調査するため一部のリポジトリを非公開にした。最優先事項は顧客とエコシステム全体の保護だ」との声明を出した。The Hacker Newsによれば、agent-frameworkはMicrosoft関連のPyPIパッケージが改ざんされた2026年2件目の事例で、同年5月にも「durabletask」パッケージが同様の手口でハイジャックされている。

研究者は、クラウドのビルド環境で発行される短命なトークンほど、窃取後すぐに悪用価値が高いと指摘しており、CI/CDパイプラインでの影響を特に警戒すべきとしている。影響を受けた可能性のある利用者には、該当ホストやCI/CDランナーの隔離、クリーンな環境からの1.26.0への固定インストール、プロキシ・DNSログでの不正エンドポイントへの通信有無の確認、Azure IDのサインインログ点検、そしてAzureやGitHub、AWS、Docker、Hugging Face等の認証情報の全面的なローテーションが強く推奨されている。
