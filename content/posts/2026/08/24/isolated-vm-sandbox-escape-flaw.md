---
date: "2026-08-24T02:04:01+09:00"
title: "isolated-vmに型混同の重大脆弱性、n8nなどAI基盤で広く使われるJSサンドボックスがRCEの危機に"
description: "Node.js向けJavaScriptサンドボックスライブラリisolated-vmに、サンドボックス内コードがホストプロセスのメモリを破壊しRCEにつながりうる型混同の脆弱性が見つかり、修正版が公開された。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/08/isolated-vm-flaw-lets-sandboxed.html"
  - "https://www.securityweek.com/critical-isolated-vm-vulnerability-leads-to-rce-on-host/"
  - "https://devops.com/critical-flaw-in-isolated-vm-can-lead-to-sandbox-escape-rce-threat/"
---

## 概要

Node.js向けのJavaScriptサンドボックスライブラリ「isolated-vm」に、サンドボックス内で実行される信頼できないコードがホストプロセスのメモリを破壊し、最終的にリモートコード実行(RCE)につながりうる重大な脆弱性が発見された。脆弱性はGHSA-864f-rcv7-6rh4として追跡されており、本稿執筆時点でCVE番号はまだ割り当てられていない。発見したのはEndor Labsのシニアセキュリティ研究者Cristian-Alexandru Staicu氏で、影響を受けるのは7.0.0以下のすべてのバージョン。修正版として6.2.0および7.0.1が2026年8月にリリースされている。isolated-vmはn8n、Mastra、Sim.ai、Activepiecesなど、AIエージェントやワークフロー自動化基盤を含む多数のプロジェクトで利用されており(npmでの週間ダウンロード数は100万近くに上る)、影響範囲は広い。

## 技術的な詳細

脆弱性の原因は、ホストとサンドボックス間でデータを安全にやり取りする役割を持つ「ExternalCopy」の`transferList`オプション処理にある。ExternalCopyのコンストラクタはバイト配列のリストを検証と転送の2段階で処理するが、2回目の転送時に1回目の検証結果を再検証せずに信頼してしまう、いわゆるTOCTOU(Time-Of-Check to Time-Of-Use)型の型混同バグとなっている。攻撃者はゲッター関数を悪用し、検証時には正規のArrayBufferを返しつつ転送時には別のデータに差し替えることで、任意のポインタを参照させメモリを破壊できる。ExternalCopy自体はホスト側からのみ呼び出せるが、サンドボックス内から呼び出せる`ivm.Reference`(ホストのオブジェクトをサンドボックスに公開する仕組み)を介して悪意あるtransferListを構築し、この脆弱性を誘発できるという。

## 影響範囲と対応

Staicu氏によれば、悪用の最小限の影響は制御されたメモリクラッシュによるサービス拒否(DoS)だが、最大では制御フローの乗っ取りによりホスト上でのRCEを引き起こす可能性があるとされる。Staicu氏は、V8のIsolate境界そのもの、つまり「分離のプリミティブ」自体は健全であり、破損が起きたのはその境界を越えて値をマーシャリングするC++バインディング層だったと説明している。修正版のパッチは、コピー処理中にユーザーのJavaScriptが実行されないようにすることでこの問題を防いでいる。サンドボックス内で信頼できないコードを実行し、Referenceを共有する構成を採用しているシステムはすべて影響を受ける可能性があるため、isolated-vmを利用する開発者には直ちに6.2.0または7.0.1へアップグレードし、サンドボックスの設定と挙動を改めて検証することが呼びかけられている。
