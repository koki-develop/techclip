---
date: "2026-10-15T08:11:04+09:00"
title: "Microsoft・Marvell・Oracleが「Project Tessera」発表、Azure統合HSMの仕様を完全オープンソース化しOCPで標準化"
description: "Microsoft、Marvell、OracleがAzureの統合型HSM技術を「Project Tessera」として完全オープンソース化し、OCPに新設したワーキンググループでFIPS 140-3 Level 3準拠のデータセンター向けハードウェアセキュリティ標準の策定を進める。"
tags:
  - OSS
  - Cloud
  - Security
references:
  - "https://azure.microsoft.com/en-us/blog/advancing-hardware-security-with-open-source-integrated-hsm-technology/"
  - "https://www.marvell.com/company/newsroom/marvell-microsoft-oracle-ocp-data-center-hardware-security.html"
  - "https://www.thefastmode.com/technology-solutions/51015-marvell-microsoft-and-oracle-collaborate-on-cloud-hardware-security-standard"
---

## 概要

Microsoftは10月13日、サンノゼで開催されたOCP Global Summitにおいて、MarvellおよびOracle、Open Compute Project(OCP)と共同で「Project Tessera」を発表した。これはAzureサーバーに組み込まれている統合ハードウェアセキュリティモジュール(HSM)のアーキテクチャ、仕様、プロトコル、ドライバ、ソフトウェア、ファームウェア、さらには再現可能なビルド環境までを完全にオープンソース化する取り組みである。3社はOCPのSecurity Track傘下に新たなワーキンググループを設立し、NIST FIPS 140-3 Level 3準拠を目標とする統合HSMの業界標準仕様の策定に着手した。仕様の初版はOCP Global Summit(10月12〜15日)で公開され、バージョン1.0はこの後に発表される予定で、関連する仕様・ソフトウェア・ファームウェアはGitHubの「TesseraHSM」リポジトリで公開されている。

## 統合HSMが解決する課題

従来のクラウドおよびハイパースケールデータセンターでは、ネットワーク接続型のHSM、あるいはソフトウェアのみによる鍵管理に依存するのが一般的だった。この方式では暗号鍵がネットワークを経由して移動したり、保護されていないメモリ上に存在したりするリスクが避けられない。Project Tesseraが採用する「ワークロード・アタッチド」型の統合HSMは、暗号処理をデータが実際に処理される場所の近くで実行しつつ、鍵自体はハードウェアのセキュリティ境界内に留め続ける設計を取る。これによりサーバーレベルでの安全な鍵キャッシングとライフサイクル管理が可能になり、ネットワーク遅延の削減とスケーラビリティの向上も見込めるという。展開モデルとしては、最大限の保証を提供する専用ハードウェア型のほか、AMD SEV-SNP環境上でユニカーネル型ファームウェアを動かす機密コンピューティング型、専用HSMを持たないシステムにも保護を拡張する仮想化型の3種類が想定されている。

## 標準化の狙いと技術実証

この取り組みの背景には、AIによる攻撃で脆弱性発見から悪用までの時間が急速に短縮されていることと、将来の量子コンピュータが既存の暗号方式を無効化しうるという2つの脅威への備えがある。MicrosoftのCTOであるMark Russinovich氏は、「AIと量子技術の進展により、デジタルインフラの中核である鍵と認証情報を守ることがこれまで以上に重要になっている」と述べた。MarvellのシニアバイスプレジデントであるCary Ussery氏も、統合HSMによって暗号鍵操作をワークロードの実行箇所そのもので行えるようにし、この機能を業界全体に提供すると説明している。実証として、MicrosoftとMarvellはTesseraと同社のLiquidSecurity 2との間でHSMパーティションのクローニングを行い、異なるベンダーのHSMがポスト量子暗号プロトコルを用いて単一のセキュリティドメイン内で相互運用できることを示した。

## 今後の見通し

Project Tesseraは、ゼロトラストアーキテクチャの要件や各種規制コンプライアンスに対応しながら、業界全体でのポスト量子暗号移行を後押しすることを目指している。仕様やファームウェアが完全にオープンソース化されることで、特定ベンダーに依存しないハードウェア鍵管理の実装がデータセンター事業者やハードウェアベンダーに広がる可能性がある。OCPでの標準化作業は今後も継続し、バージョン1.0仕様の発表に向けてMicrosoft、Marvell、Oracleを中心とするワーキンググループでの議論が進められる見通しだ。
