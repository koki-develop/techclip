---
date: "2026-11-20T18:09:22+09:00"
title: "MicrosoftとIntelがAzure向け協業を拡大、EMIBパッケージング初採用とXeon「Diamond Rapids」複数年供給で合意"
description: "MicrosoftとIntelが長期協業を拡大し、Azure専用シリコンでIntel FoundryのEMIBパッケージング技術を初採用、次世代Xeon「Diamond Rapids」の複数年供給にも合意した。"
tags:
  - Cloud
references:
  - "https://news.microsoft.com/source/2026/11/18/microsoft-and-intel-deepen-collaboration-to-deliver-differentiated-azure-infrastructure/"
  - "https://www.intel.com/content/www/us/en/newsroom/news/corporate/microsoft-azure-infrastructure-collaboration.html"
  - "https://www.digitimes.com/news/a20261119VL209/microsoft-intel-azure-packaging-intel-foundry.html"
---

## 概要

MicrosoftとIntelは11月18日、数十年に及ぶ協業関係をさらに拡大し、Azure専用インフラの差別化に向けた長期契約を結んだと発表した。目玉となるのは、Intel Foundryの先進パッケージング技術「EMIB」(Embedded Multi-die Interconnect Bridge)をAzureのファーストパーティ製シリコンに初めて採用することだ。あわせて、次世代サーバー向けCPU、コードネーム「Diamond Rapids」を含む複数年にわたるIntel Xeonの供給容量確保でも合意している。Microsoft Azure System & Architecture担当副社長のSaurabh Dighe氏は、両社の協業によって「シリコンとシステムエンジニアリングを連携させ、業界を前進させる」ことができると述べ、Intel FoundryのエグゼクティブバイスプレジデントであるNaga Chandrasekaran氏も、EMIBの活用により「AI時代に求められる製造規模と異種統合の柔軟性を兼ね備える」ことができると強調した。

## 技術的な詳細

EMIBは複数のダイを同一パッケージ内で高密度に接続する異種統合(heterogeneous integration)技術で、Microsoftはこれを採用する最初の企業として公にコミットした初の事例となる。これにより製造スケールと設計上の柔軟性を両立できるとされる。メモリ面では、CXL(Compute Express Link)メモリとIntelの「Flat Memory Mode」を組み合わせたAzure M-series v4仮想マシンで、最も要求の厳しいワークロードにおいてメモリ性能が最大2.3倍向上するという。さらに、Intel QuickAssist Technology(QAT)によるSQLバックアップの最大2.5倍高速化や、Intel Trust Domain Extensions(TDX)を用いた機密VMのメモリ・CPUレジスタ暗号化といった機能強化も盛り込まれている。

## Intelにとっての意味合い

Digitimesの報道(本文は有料会員限定のため見出しのみ確認)は、この提携が「Intelに収益よりも信頼性をもたらす」と分析している。MicrosoftがEMIBの採用を公表した最初の大手顧客となったことは、売上規模そのものよりも、Intel Foundryの先進パッケージング技術が大手ハイパースケーラーに通用する水準にあることを示す証明材料としての意味合いが大きいとみられる。AI向け半導体の受託製造で存在感を示そうとするIntelにとって、Microsoftという看板顧客の存在は今後の受注拡大に向けた重要な足がかりとなりそうだ。

## 今後の見通し

両社は今回の契約を、シリコン・パッケージング・メモリ・ソフトウェアを一体で最適化していくための第一歩と位置付けている。AIワークロードの急増に対応するため、より予測可能でスケーラブル、かつ耐障害性の高いインフラ基盤をAzure上で構築していく方針だ。次世代Xeon「Diamond Rapids」の投入や複数年供給の確保は、Microsoftにとって調達の安定性を高める一方、Intelにとってはファウンドリ事業とCPU事業の双方で長期的な需要の裏付けを得る動きとなる。
