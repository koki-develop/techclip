---
date: "2026-04-03T18:17:14+09:00"
title: "GoogleドライブのAIランサムウェア検出が一般提供開始、有料ユーザーにデフォルト有効化でベータ比14倍の検出力"
description: "GoogleはAIを活用したGoogleドライブのランサムウェア検出・ファイル復元機能を一般提供開始し、有料ユーザー向けにデフォルトで有効化した。"
tags:
  - Security
  - Cloud
references:
  - "https://www.bleepingcomputer.com/news/security/google-drive-ransomware-detection-now-on-by-default-for-paying-users/"
  - "https://workspaceupdates.googleblog.com/2026/03/ransomware-detection-and-file-restoration-for-Google-Drive-now-generally-available.html"
  - "https://www.techrepublic.com/article/news-google-drive-ransomware-detection-file-recovery/"
---

## 概要

GoogleはAIを活用したGoogleドライブのランサムウェア検出機能を2026年4月に一般提供（GA）開始し、ビジネス・エンタープライズ・教育・フロントラインの各ライセンスを含む有料ユーザー全員に対してデフォルトで有効化した。この機能はデスクトップからDriveへの同期時にファイルをスキャンし、暗号化されたファイルを検出すると即座にデスクトップ同期を停止する仕組みだ。検出時にはユーザーへのメール通知とDrive内アラート、そして管理者向けのGoogle管理コンソールへの通知が行われる。

ファイル復元機能はGoogle Workspaceユーザーだけでなく、個人サブスクライバーや個人アカウント利用者にも提供される。検出アラートを利用するにはGoogle Drive デスクトップアプリ v.114以降が必要だ。

## 技術的な詳細と性能向上

Googleによれば、今回一般提供されたAIモデルはベータ版と比較して「14倍多くの感染を検出」できるようになっており、より多くのランサムウェアの亜種を素早く検出できるという。機能はGoogle Driveのインフラに直接統合されており、サードパーティ製ツールや複雑な設定を必要とせず、既存のワークフローを阻害することなく透過的に動作するよう設計されている。

組織の管理者は必要に応じて、管理コンソールの「アプリ > Google Workspace > ドライブとドキュメントの設定 > マルウェアとランサムウェア」からこの機能を無効化することができる。なお、古いバージョンのアプリを使用していても、ランサムウェア検出時のファイル同期一時停止は継続して機能する。

## 背景と競合状況

この機能は2025年9月に最初に発表され、同年10月からGoogle Workspaceの一部ユーザーを対象にベータ提供が開始されていた。今回のGA移行により、対象ユーザーが大幅に拡大した。クラウドストレージにおけるランサムウェア対策はMicrosoft OneDriveやDropboxも同様の機能を有料プラン向けに提供しており、主要クラウドストレージサービス間でのセキュリティ機能の標準化が進んでいる。企業や教育機関が機密文書やビジネスクリティカルな情報をクラウドに保存する機会が増える中、こうした組み込み型のランサムウェア対策は重要性を増している。
