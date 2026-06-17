---
date: "2026-06-18T02:56:27+09:00"
title: "Windows DefenderのゼロデイRoguePlanet（CVE-2026-50656）、完全パッチ済み環境でもSYSTEM権限昇格が可能——Microsoftが修正対応中"
description: "Microsoftのマルウェア対策エンジンにレースコンディションを悪用するゼロデイ脆弱性「RoguePlanet」（CVE-2026-50656）が公開され、完全にパッチ適用済みのWindows 10/11端末でもSYSTEM権限を取得できることが確認された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-working-on-defender-patch-for-rogueplanet-zero-day/"
---

## 概要

セキュリティ研究者「Nightmare Eclipse」は、Microsoft Defenderのマルウェア対策エンジン（Malware Protection Engine）に存在するゼロデイ権限昇格脆弱性「RoguePlanet」のPoC（概念実証コード）を公開した。この脆弱性はCVE-2026-50656として追跡されており、完全にパッチが適用された最新のWindows 10およびWindows 11上でも、SYSTEM権限を持つコマンドプロンプトを起動できる。Microsoftはすでに脆弱性を認識しており、「高品質なセキュリティアップデートの提供に向けて作業中」と声明を出した。

## 技術的な詳細

RoguePlanetの本質はレースコンディションであり、タイミング次第でSYSTEM権限のシェルを取得できる。研究者によれば「エクスプロイトはレースコンディションのため成否がある。一部の機器では100%の成功率を達成できたが、機器によっては安定しないこともある」とのことで、環境依存の再現性を持つ点が特徴だ。またリアルタイム保護の有効・無効を問わず機能することが確認されており、単純な保護機能の無効化では根本的な緩和とならない。

## 開示の背景と研究者との対立

今回の公開は、MicrosoftのバグバウンティおよびVDP（脆弱性開示プログラム）をめぐる研究者との継続的な対立の一部として行われた。Nightmare Eclipseは過去にも「BlueHammer」「RedSun」「GreenPlasma」「MiniPlasma」「YellowKey」など複数のWindowsゼロデイを公開しており、GitHubおよびGitLabからリポジトリを削除されたと主張した後、自己管理のGitリポジトリ上でPoCを公開している。なお、MicrosoftはCVE-2026-50656の公式通知において元の研究者をクレジットしていない。

## 現在の対応状況

Microsoftは「本脆弱性に対処する高品質なセキュリティアップデートの提供に向けて作業中」とし、アップデートが利用可能になり次第CVE上で情報を提供するとしているが、公開時期は明らかにしていない。現時点で記事内では暫定的な緩和策や設定変更は案内されておらず、根本的な対処にはMicrosoftの修正パッチの適用が必要となる。企業・個人ユーザーともに、Microsoftのセキュリティ情報を継続的に確認し、パッチの公開次第、速やかに適用することが強く推奨される。
