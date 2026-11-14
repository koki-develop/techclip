---
date: "2026-11-15T08:06:47+09:00"
title: "Windows CLFSのゼロデイ「SignDrop」、標準ユーザーからSYSTEM権限奪取のPoCが公開"
description: "研究者Nightmare EclipseがWindows CLFSドライバーの認証ファイル生成処理を突く未修正の脆弱性「SignDrop」の実証コードを公開し、Microsoftは対応を調査中としている。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/11/new-signdrop-zero-day-exploit-turns.html"
  - "https://gbhackers.com/new-windows-signdrop-zero-day/"
  - "https://www.securityweek.com/nightmare-eclipse-drops-windows-zero-day-exploit-signdrop/"
---

## 概要

セキュリティ研究者Nightmare Eclipse(Abdelhamid Naceri、一部報道ではMSNightmareとも)が、Windowsの共通ログファイルシステム(CLFS)ドライバーを突くゼロデイ脆弱性「SignDrop」の実証コード(PoC)をGitHubで公開した。標準ユーザー権限で動作するプロセスから、CLFSドライバーの処理を悪用してSYSTEM権限での任意ファイル書き込みを引き起こし、最終的にSYSTEMシェルを獲得できるというもので、記事公開時点でCVE番号は割り当てられておらず、Microsoftも修正パッチを提供していない。対象はWindows 11 26H2、Windows 11 26H2 Experimental、Windows Server 2025 Experimentalで、稼働開始から90日以上経過した環境も含めると世界のWindows端末の約8割が影響範囲に該当するとの推計も報じられている。

## 技術的な詳細

CLFSは2025年10月の更新で、過去のメモリ破壊系脆弱性(CVE-2025-29824など)への対策として、ログファイルの改ざんを検知する「認証(authentication)」機構を導入した。ログを開く際にドライバーは対応する認証ファイル(`.cnpf`)の有無を検証し、存在しない場合はSYSTEM権限で新規生成する。SignDropはこの生成処理の検証漏れを突く。攻撃者はまず`AddLogContainer`APIで元のログに空のコンテナを追加し、オブジェクトマネージャーのシンボリックリンクを使ってファイル生成先を自分が制御するパスへすり替える。そのうえで、署名更新用RPCインターフェース(`ServerMpUpdateEngineSignature`)経由でMicrosoft Defenderに当該ログを開かせると、Defenderは特権プロセスとしてCLFSの認証ファイル生成処理を起動することになり、CLFSは検証なしに攻撃者が指定した場所へSYSTEM権限で`.cnpf`ファイルを書き込んでしまう。生成されたファイルは元ファイルのDACL(攻撃者が制御)を継承するため、これを足掛かりに任意コード実行からSYSTEMシェル奪取へと連鎖させられる。ある研究者は「Microsoft側の実装はすべて正しく行われているが、そのロジック自体が悪用を許してしまう」とコメントしており、個々の処理は仕様通りでも、組み合わせると権限昇格経路が生まれる点が特徴となっている。

## 影響範囲と対応状況

脆弱性の悪用には、レジストリの`HKLM\SYSTEM\CurrentControlSet\Services\CLFS\Authentication`でCLFS認証モードが「enforced(0)」または「learning(1)」に設定されていることが条件となる。この設定は多くの環境で既定となっているとみられ、報道によれば該当するシステムは世界のWindows環境の約8割に及ぶとされる。なお認証モードを無効化することは、SignDropが対策しようとしていた既存のメモリ破壊系脆弱性を再び露呈させるリスクがあるため推奨されていない。セキュリティ企業Cyderesは公開されたPoCを実際にコンパイルして動作を確認しており、実証性は高いと見られる一方、現時点で野放し(in the wild)での悪用報告や、米CISAの既知悪用脆弱性(KEV)カタログへの登録は確認されていない。Microsoftは「報告された脆弱性を現在調査しており、必要に応じて影響を受ける製品の更新に向けた対応を進める」との声明を出しており、Defenderについては本脆弱性の悪用に関連する権限昇格の挙動を検知・ブロックし、アラートを発するとしている。パッチ提供までの間、組織には標準ユーザー権限の最小化、Defenderや特権プロセスによる予期しない`.cnpf`ファイル生成の監視、`ERROR_LOG_METADATA_CORRUPT`エラーの発生有無の確認といった暫定的な対策が呼びかけられている。
