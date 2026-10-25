---
date: "2026-10-26T08:10:28+09:00"
title: "パッチ適用済みWindowsでもSecure Boot回避、APT41系UEFIブートキット「BlackX」をKasperskyが発見"
description: "Kasperskyが中央アジアの外交機関を標的とした新型UEFIブートキット「BlackX」を発見、完全にパッチ適用済みのWindowsでもBaton Drop脆弱性を悪用してSecure Bootを回避する手口が明らかになった。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/10/blackx-uefi-bootkit-bypasses-secure.html"
  - "https://www.bleepingcomputer.com/news/security/blackx-uefi-bootkit-exploits-baton-drop-flaw-to-bypass-secure-boot/"
  - "https://securelist.com/uefi-bootkit-blackx/121539/"
---

## 概要

Kasperskyの調査チーム(GReAT)は、中央アジアの外交機関を標的とした新型UEFIブートキット「BlackX」を発見した。2026年初頭に実行されたこの攻撃では、タジキスタン、ウズベキスタン、トルクメニスタンの外交機関が狙われ、2022年に話題となったブートキット「BlackLotus」と非常に類似した実装でSecure Bootを回避する手口が使われている。特に注目すべきは、被害を受けたシステムがいずれも「完全にパッチ適用済み」のWindowsだったという点だ。原因は脆弱性そのものではなく、脆弱性に対するMicrosoftのパッチの設計にある。Kaspersky GReATは中程度の確度で、中国系の国家支援グループAPT41との関連を指摘している。

## Baton Drop脆弱性とパッチの構造的な欠陥

BlackXが悪用するのは、2022年に報告された既知の脆弱性「Baton Drop」(CVE-2022-21894)だ。この脆弱性は、署名が失効していない古い「Windows Production PCA 2011」証明書を利用してSecure Bootのチェックを回避できるというもので、BlackLotusが初めて実証したことで知られる。問題は、Microsoftが提供した修正パッチが、この証明書を自動的には失効させない設計になっていたことだ。失効を有効化するには、管理者がレジストリフラグを設定し、スケジュール済みタスク「Secure-Boot-Update」を実行するという手動の作業が必要であり、この手順が広く認知されていなかった。証明書自体は2026年10月19日に期限切れとなったが、依然としてブロックリストには登録されていない。つまり、Windows Updateを適用しているだけでは、この手口への対策にならないという構造的な欠陥が存在する。

## BlackXの技術的な仕組み

BlackXの感染プロセスは、インストーラー実行ファイル「inst.exe」と、RC4で暗号化されたファイル「PVMDIJGKAX2」を通じて行われる。ブートキットが展開するペイロードは大きく2種類に分かれる。1つは、中国の組織「温江区明宇网络技术服务工作室」名義の証明書で署名されたカーネルドライバで、Kaspersky製品やAvastなどのセキュリティソフトを検知時に選択的に無効化し、ファイルアクセスを遮断する。もう1つはユーザーモードで動作するペイロード群で、Google Drive、OneDrive、Yandex.Diskといった正規のクラウドストレージサービスをC2(コマンド&コントロール)チャネルとして利用するRAT(遠隔操作ツール)と、OLLVMで難読化されたDLL「OxiDLLRunner」が含まれる。OxiDLLRunnerはRust製のペイロードを読み込み、独自ドメイン「archivetj.com」と通信する。BlackLotusのソースコードは公開されていないため、Kasperskyは攻撃者がリバースエンジニアリングを行うか、サイバー犯罪者からソースコードを購入した可能性があるとみている。

## APT41との関連性

Kaspersky GReATは、複数の状況証拠からBlackXを中国系の国家支援グループAPT41に中程度の確度で帰属させている。根拠の一つは、2026年6月にESETが報告した「FishMonger」(APT41関連と推定されるグループ)によるカーネルインプラントの事例で、PDBパス中に識別子「xdd」が含まれていたことだ。この「xdd」という文字列はBlackXの解析時にも複数回確認されている。さらに、正規実行ファイルを利用したDLLサイドローディングの手口や暗号化ファイルの使用方法が中国系脅威アクターに共通して見られる特徴と一致すること、難読化に使われたOLLVMが中国系アクターの間で広く使われているツールであることも、帰属の判断材料となっている。

## 今後の対策

この事例が示すのは、既知の脆弱性に対するパッチが適用されていても、パッチの設計自体に不備があれば攻撃を防げないという構造的なリスクだ。Microsoftは証明書の失効について、依然として強制的な適用段階を実装していない。Kasperskyは、管理者が「Windows Production PCA 2011」証明書を手動でブロックリストに追加する必要があると注意を呼びかけるとともに、エクスプロイト自体の実行を検知・防止する「Exploit Prevention」のような機能の重要性を強調している。BlackLotus以降、UEFIブートキットの実装やソースコードが闇市場を通じて流通・再利用される傾向が続いており、同様の手口を使う攻撃が他の地域や業界にも拡大する可能性がある。
