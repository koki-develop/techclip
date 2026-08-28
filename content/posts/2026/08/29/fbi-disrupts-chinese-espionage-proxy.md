---
date: "2026-08-29T08:09:51+09:00"
title: "FBI、中国国家系ハッカー集団の偵察・プロキシ網「QScan」「QTRouter」を摘発しドメイン押収"
description: "FBIと米司法省は中国国家系脅威グループQTFYが運用する偵察ツール「QScan」とプロキシ管理網「QTRouter」の基盤ドメインを押収し、NASAや米上院などを狙ったサイバースパイ活動用インフラを無力化した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/fbi-disrupts-proxy-network-enabling-chinese-espionage-operations/"
  - "https://techcrunch.com/2026/08/26/us-seizes-domains-of-chinese-botnet-used-to-hack-nasa-justice-department-and-the-senate/"
  - "https://www.theregister.com/security/2026/08/27/fbi-seizes-hacking-tools-it-says-china-used-to-attack-nasa-doe-us-senate-and-other-critical-networks/5292742"
---

## 概要

FBIと米司法省は8月26日、中国国家系の脅威グループ「QTFY」(別名QT/QTCYBER)が運用するサイバースパイ活動用インフラを摘発したと発表した。連邦裁判所の許可のもと、偵察ツール「QScan」とプロキシ管理網「QTRouter」に組み込まれた3つのドメイン(qtproxy.xyz、qt-proxy.org、qt-team.com)を押収し、両ハッキングツールを機能停止に追い込んだ。QTFYは南京の企業Nanjing Xinjiuwei Network Technologyと関連し、NASA、エネルギー省、司法省、保健福祉省、国立衛生研究所、連邦準備制度、米上院など米国の重要機関を標的にしてきたとされる。

## QScanとQTRouterの仕組み

QScanは開放ポートやアプリケーションバナー、OSフィンガープリント、設定情報を収集し、価値の高い標的を特定する偵察プラットフォームであると同時に、脆弱性を突いてIoTデバイスに自動感染し、それらをQTRouterネットワークへ組み込むマルウェアでもある。QTRouterは、こうして侵害されたIoTデバイスや商用プロキシサービス、レンタル仮想サーバーからなる難読化ネットワークで、攻撃者の発信元を隠蔽する。QTFYは商用プロキシサービス「fastlink.ws」のノードへのプレミアムアクセスを購入し、スパイ活動の通信を一般消費者のプロキシ利用に紛れ込ませつつ、出口インフラを自動的にローテーションさせていた。この管理には「QTProxy」というツールと、物理デバイスの「QTRouter」自体がノードアクセスとルート設定の管理に使われていたという。米司法省によれば、押収されたドメインはボットネットのコードにハードコードされており、通信と運用に不可欠だったため、押収によりインフラは機能しなくなった。

## 標的と攻撃の履歴、国家との関係

活動は2018年頃から続いており、2019年8月にはIvanti Pulse Secureの脆弱性(CVE-2019-11510)を突いてNASAを攻撃、2020年には新型コロナ禍のオハイオ州の医療センターを標的にし、2024年にはIvanti Cloud Services Applianceのゼロデイ脆弱性を使いエネルギー省傘下の3つの国立研究所を侵害したとされる。2026年には米上院への走査活動も確認されたが、侵入には至らなかったとNSAは説明している。裁判資料によれば、QTFYには中国人民解放軍(PLA)の元関係者が含まれ、Nanjing Xinjiuweiは中国国家安全部(MSS)から支払いを受けており、中国政府の意向を受けて活動していたことを示す証拠とされる。同社はMSSのハッカーに対しボットネットのサービスを提供する「顧客」関係にもあったという。

## セキュリティ企業の関与と今後の課題

ネットワーク基盤事業者Lumenは過去1年にわたり標的化の傾向を観測し、脅威インテリジェンスをFBIの捜査に提供した。またBlack Lotus Labsは既知のクォーターマスター拠点へのトラフィックをヌルルーティングする形でインフラの一部を無力化したが、研究者らは「動的に切り替わる商用プロキシサービス」という性質上、静的なブロックだけでは不十分だと警告している。組織にはルーターやファイアウォール、IoTデバイスの更新に加え、CISAおよび英NCSCが公表する中国系脅威への対策指針に従うことが推奨されている。今回の摘発は、2025年のPlugXマルウェア除去、2024年のFlax Typhoonボットネット摘発、2023~2024年のVolt Typhoon阻止など、FBIによる一連の中国国家系インフラ解体作戦の延長線上にある。ただしVolt Typhoonは阻止後も再興し、2026年6月時点で感染デバイス数が1,500台に達したとの報告もあり、今回のQTFY摘発についても同様の再興リスクへの警戒が求められる。
