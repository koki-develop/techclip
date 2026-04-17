---
date: "2026-04-17T10:38:05+09:00"
title: "CERT-UA、ウクライナ医療・政府機関を狙うUAC-0247のマルウェアキャンペーンを公開"
description: "ウクライナのCERT-UAが、2026年3〜4月にかけて政府機関・医療施設を標的にしたサイバー攻撃キャンペーンUAC-0247の詳細を発表した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/uac-0247-targets-ukrainian-clinics-and.html"
  - "https://securityaffairs.com/190875/apt/from-clinics-to-government-uac-0247-expands-cyber-campaign-across-ukraine.html"
  - "https://thecyberexpress.com/cyberattacks-on-hospitals-by-uac-0247-hackers/"
  - "https://cybersecuritynews.com/new-uac-0247-campaign-steals-browser-and-whatsapp-data/"
---

## 概要

ウクライナのコンピュータ緊急対応チーム（CERT-UA）は2026年4月、脅威クラスター「UAC-0247」による標的型サイバー攻撃キャンペーンの詳細を公開した。このキャンペーンは2026年3月から4月にかけて活発に展開され、政府機関・自治体の医療施設（クリニック、救急病院など）を主な標的としている。攻撃者は人道支援提案を装ったフィッシングメールを送りつけ、被害者を悪意のあるサイトへ誘導する手口を用いた。誘導先はXSS脆弱性を突いて侵害された正規サイト、またはAIツールで生成された偽サイトのいずれかだという。

## 攻撃チェーンと使用マルウェア

攻撃は多段階の感染フローを持つ。フィッシングメールのリンクをクリックした被害者は、Windowsショートカット（LNK）ファイルをダウンロード・実行する。このLNKファイルが`mshta.exe`を通じてリモートのHTA（HTMLアプリケーション）を呼び出し、囮フォームを表示しながら裏でシェルコードを正規プロセス（`runtimeBroker.exe`など）に注入する。最終ペイロードは独自の実行ファイル形式を持つ2段階ローダーで配布され、追加の圧縮と暗号化が施されている。

使用されたカスタムマルウェアは3種類確認されている。

- **RAVENSHELL** — TCPリバースシェルで、XOR暗号化（キー: `01 01 02 03 74 15 04 FF EE`）を用いてC2サーバーと通信し、`cmd.exe`経由でコマンドを実行する。
- **AGINGFLY** — C#製のリモートアクセスツール（RAT）。AES-CBC暗号化されたWebSocketで通信し、コマンド機能をサーバーから動的に取得する。キーロガー、ファイルダウンロード、スクリーンショット取得などの機能を持つ。
- **SILENTLOOP** — PowerShellスクリプト。コマンド実行・自動更新に加え、Telegramチャンネルを利用したC2サーバーIPアドレスの取得とフォールバックC2メカニズムを備える。

## オープンソースツールの悪用とデータ窃取

カスタムマルウェアに加え、攻撃者は複数のオープンソースツールを組み合わせた。ChromeのApp-Bound暗号化を回避してCookieやパスワードを収集する**CHROMELEVATOR**、WhatsApp Webのデータベースを復号する**ZAPIXDESK**、ネットワーク偵察用の**RustScan**、リバースTCP/TLSトンネルを確立する**Ligolo-Ng**とTCP/UDPトンネリングツールの**Chisel**、そして改変されたWireGuard実行ファイルに埋め込まれた暗号通貨マイナー**XMRig**がその一例だ。これらを組み合わせることで、ChromiumベースのブラウザとWhatsAppからの機密情報窃取、横展開、持続的な侵害が行われていた。

また、医療・政府機関への攻撃と並行して、2026年3月にはウクライナ国防軍の関係者がSignalプラットフォームを通じた攻撃の被害を受けた可能性も判明した。FPVドローン操作用ソフトウェアのアップデートを装ったZIPアーカイブが配布され、DLLサイドローディングによってAGINGFLYが展開された。

## CERT-UAの推奨する緩和策

CERT-UAは「LNK・HTA・JSファイルの実行を制限し、正規ユーティリティである`mshta.exe`、`powershell.exe`、`wscript.exe`の起動を制限するだけで、サイバー脅威の可能性を大幅に低減できる」と述べている。戦時下のウクライナで医療インフラや政府機関が高度な攻撃に継続的にさらされている実態が改めて浮き彫りになった事例であり、重要インフラへの攻撃に対する多層防御の重要性が示されている。
