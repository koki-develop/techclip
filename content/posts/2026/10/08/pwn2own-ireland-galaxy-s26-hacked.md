---
date: "2026-10-08T08:12:00+09:00"
title: "Pwn2Own Ireland 2026初日、Galaxy S26が3チームに攻略されIoTやAI基盤含め32件のゼロデイが披露"
description: "Pwn2Own Ireland 2026の初日、Samsung Galaxy S26が3チームにそれぞれ個別攻略されるなど合計32件のゼロデイが実演され、総額388,500ドルの賞金が支払われた。"
tags:
  - Security
references:
  - "https://www.zerodayinitiative.com/blog/2026/10/6/pwn2own-ireland-2026-day-one-results"
  - "https://www.bleepingcomputer.com/news/security/hackers-exploit-32-zero-days-on-first-day-of-pwn2own-ireland/"
  - "https://cyberinsider.com/samsung-galaxy-s26-hacked-three-times-at-pwn2own-ireland-2026/"
---

## Galaxy S26が1日で3度攻略される

Trend MicroのZero Day Initiative(ZDI)が主催するハッキングコンペティション「Pwn2Own Ireland 2026」が10月6日、アイルランド・コークで開幕した。初日には21件のエントリーが披露され（大会全体では3日間で60件を超えるエントリーが予定されており）、モバイル端末からIoT機器、AI関連基盤までを対象に合計32件のゼロデイ脆弱性が実演され、参加チームは総額388,500ドルの賞金を獲得した。中でも注目を集めたのが、同一端末であるSamsung Galaxy S26がその日のうちに3チームからそれぞれ個別の手法でハッキングされたことだ。Viettel Cyber SecurityのNguyen Thanh Datは4件の脆弱性(うち3件は既知)を組み合わせて端末を攻略し31,250ドルを獲得、Interrupt Labsも4件の脆弱性(3件のコリジョンと1件の新規ゼロデイ)を連鎖させて15,750ドルを得た。Ikotas Labsも同様に4件の脆弱性(1件は既知だが未修正)を組み合わせて攻略し、賞金は11,000ドルながらMaster of Pwnポイントは3チーム中最高の4.5点を獲得している。同じ端末が複数の異なる手法で繰り返し陥落した事実は、Samsungの修正パッチが一部の既知の問題に対処し切れていない実態を浮かび上がらせた。

## AI基盤・クラウドサービスへの攻撃も目立つ

今回の大会ではモバイル端末だけでなく、AIやクラウドの基盤サービスを狙った攻略も高額賞金で目立った。VinSOCのVũ Chí ThànhとHuỳnh Đức Tinのチームは、Oracle Autonomous AI Databaseを5件の脆弱性を用いて攻略し40,000ドルを獲得。XintのTaisic Yunは大規模言語モデルのプロキシ/ゲートウェイであるLiteLLMを攻略して同額の40,000ドルを得た。さらにIkotas Labsは、クラウドベースの開発者向けAIツールであるOpenAI Codexに対し引数インジェクション(argument injection)を用いた攻略を成功させ、こちらも40,000ドルの賞金を獲得している。これらの結果は、従来のOS・ブラウザ・ルーターといった定番ターゲットに加え、AIを組み込んだクラウドサービスや開発支援ツールが新たな攻撃対象として研究者の関心を集めていることを示している。

## IoT機器とスマートホームも標的に

IoT・スマートホーム分野では、VinSOCのチームがPhilips Hue Bridge Proスマート照明ハブに対し7件の脆弱性を連鎖させる攻略を披露し、これも40,000ドルの高額賞金を獲得した。Interrupt LabsはGarmin Index BPM(血圧計)の攻略に成功し20,000ドルを得ている。一方でBrotherやLexmarkの複合機、Google Pixel 10、Garmin Index BPMへの別チームによる挑戦、Chromaなどを対象にした攻略の試みは失敗に終わった。全体として初日の成功例のうち7件は既知の脆弱性(コリジョン)が絡んでおり、ベンダー側のパッチ適用や脆弱性管理の難しさも浮き彫りになった。

## 背景と今後の見通し

Pwn2Ownはベンダーに未知のゼロデイ脆弱性を実演形式で発見・報告させる競技会で、発見された脆弱性についてはベンダーに90日間の修正期間が与えられる仕組みになっている。前年の2025年大会では合計73件のゼロデイが披露され、1,024,750ドルが配分されており、今回の初日の388,500ドルはその規模の大きさを裏付けるペースと言える。なお賞金総額や披露件数についてはBleepingComputerが「32件・388,500ドル」、CyberInsiderがZDIの集計時点のデータとして「28件・342,500ドル」とやや異なる数字を報じており、集計時点や対象の数え方に差があるとみられる。大会は複数日程で続く予定で、初日に攻略された製品の多くはOS・クラウドサービスを問わず幅広い業界に影響するため、今後も各ベンダーの修正対応の速さが注目される。
