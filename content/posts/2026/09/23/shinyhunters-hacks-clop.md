---
date: "2026-09-23T18:14:31+09:00"
title: "恐喝集団ShinyHunters、ランサムウェアClopのリークサイトを乗っ取り「その手口」で逆恐喝"
description: "恐喝グループShinyHuntersがランサムウェア集団ClopのダークウェブリークサイトをGrav CMSの脆弱性経由で乗っ取り、八桁ドル規模の支払いを要求する異例の抗争に発展した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/shinyhunters-hacks-clop-leak-site-threatens-to-extort-ransomware-gang/"
  - "https://therecord.media/shinyhunters-clop-cyberattack-website"
  - "https://www.theregister.com/cyber-crime/2026/09/21/clop-gets-a-taste-of-its-own-medicine-after-shinyhunters-hijack-leak-site/5297702"
---

## 概要

恐喝グループShinyHuntersが週末にかけて、ランサムウェア集団Clopのダークウェブ上のリークサイトを乗っ取り、「DOMAIN SEIZED BY SHINYHUNTERS」の横断幕とともに「THIS SITE HAS BEEN PWN3D BY SHINYHUNTERES #Skids10p - Maybe don't try to threaten us next time」という改ざんメッセージを掲示した。攻撃には、サイトが利用するGrav CMSの認証不要のファイルアップロードの脆弱性が使われ、テキストファイルをアップロードする形でサイトを改ざんしたとみられる。被害企業を脅迫してきたランサムウェア集団が、今度は自らの手口を模した形で恐喝される側に回るという、サイバー犯罪者間では異例の展開となった。

## 攻撃の手口と主張される戦果

ShinyHuntersは、ソースコードやGrav CMSのプラグイン、`/var/log`以下のシステムログに加え、Torオニオンサービスの秘密鍵まで窃取したと主張している。オニオン鍵を保有していることから「たとえClopが自分たちを締め出しても意味がない」（"We have their onion keys. So if they kick us out it wouldn't matter"）とし、Clop側のオニオンアドレスを自前のサーバー上で運用できる状態にあるとしている。BleepingComputerは改ざんと初期のファイルアップロードについては確認したものの、データ窃取やオニオン鍵に関する主張自体は独自に検証できていないとしている。

## 対立の背景とオラクル製品の脆弱性を巡る先取権争い

両者の対立の根底には、2025年10月に発生したOracle E-Business Suiteを狙ったClopのキャンペーンがある。ShinyHuntersは、当該ゼロデイ脆弱性を自分たちが先に発見しTelegram上でPoCエクスプロイトを公開していたところ、Clopがそれを無断で入手して企業ネットワークへの攻撃に悪用したと主張している。さらにShinyHuntersは、Clop側の関係者からメンバーに対する暴力的な脅迫を受けたとも主張しており、金銭以外の遺恨も対立の引き金になったとみられる。

## エスカレートする恐喝要求とClopの反応

ShinyHuntersは当初、自称純資産の「2.333%」に相当する八桁ドル規模の支払いを要求していたが、その後「EBSキャンペーンで得た金額全額に利息を上乗せして払え」（"all the money you made off the EBS campaign plus more AND WITH INTEREST"）へと要求をエスカレートさせた。さらに公の謝罪も新たな要求として追加し、応じなければ24時間ごとに要求額を引き上げると通告している。応じない場合は、Clopが過去に恐喝した企業の支払い記録（被害企業名、支払額、ビットコインアドレスを含む）を公開すると脅しており、これが実現すればひそかに身代金を支払い水面下で交渉が終わったと考えていた企業にとって新たな信用失墜リスクとなる。Clop側は「Shiny Hunters we trying to reach you Your email does not work」などとメールでの疎通不能を訴える形で接触を試みており、交渉のテーブルに着こうとする姿勢もうかがえる。

## 業界への影響と今後の見通し

Clopは2023年のMOVEit攻撃キャンペーンで数千の組織、数千万人規模の情報流出に関与したとされる、サイバー犯罪史上でも有数の悪名高い恐喝集団である。そうした「大物」がより小規模な恐喝グループにインフラを乗っ取られたという事実は、犯罪組織間の力学における注目すべき変化を示している。リークサイトはランサムウェア集団にとって、被害者への圧力手段であると同時に自らの実力を誇示する場でもあり、それが侵害されたこと自体が組織としての信用と運用体制の脆弱性を露呈する結果となった。要求のエスカレートぶりと24時間ごとの引き上げ通告からは、交渉が不調に終われば事態がさらに深刻化する可能性が示唆されており、今後Clopの被害企業の支払い履歴が実際に公開されるかどうかが焦点となる。
