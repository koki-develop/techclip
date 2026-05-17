---
date: "2026-05-18T02:26:19+09:00"
title: "Pwn2Own Berlin 2026初日：Edge・Windows 11・AIゲートウェイで24件のゼロデイを実証、52万3,000ドルを授与"
description: "Pwn2Own Berlin 2026の初日、セキュリティ研究者が24件のゼロデイ脆弱性を実証して合計52万3,000ドルを獲得した。Microsoft EdgeのサンドボックスエスケープやLiteLLM・OpenAI CodexなどAIプラットフォームへの攻撃が特に注目を集めた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/windows-11-and-microsoft-edge-hacked-on-first-day-of-pwn2own-berlin-2026/"
  - "https://cybersecuritynews.com/pwn2own-berlin-2026/"
  - "https://securityaffairs.com/192183/hacking/pwn2own-berlin-2026-day-one-523000-paid-out-ai-products-fall.html"
---

## 概要

2026年5月14日、OffensiveCon会場で開幕したPwn2Own Berlin 2026の初日に、セキュリティ研究者が24件のゼロデイ脆弱性を実証し、合計52万3,000ドルの賞金が支払われた。22エントリーがMicrosoft Edge、Windows 11、各種AIプラットフォームなど広く使われる製品を標的とし、賞金総額100万ドル以上が用意されたコンテストにおいて幸先の良い初日となった。昨年のベルリン大会の初日と比較しても高水準であり、大会3日間の合計では2025年の107万8,750ドルを超えるペースとなっている。

## 最大の成果：DEVCOREによるEdgeサンドボックスエスケープ

最高額となる17万5,000ドルを獲得したのは、DEVCOREリサーチチームのOrange Tsai（Cheng-Da Tsai）氏だ。同氏はMicrosoft Edgeに対して4つのロジックバグを連鎖させたエクスプロイトでサンドボックスエスケープを達成した。メモリ破壊を用いず純粋にロジックの欠陥だけを組み合わせた点が技術的に高く評価されており、17.5 Master of Pwn ポイントも獲得。DEVCOREチームは初日終了時点でチームトータル20万5,000ドルを積み上げ、リーダーボード首位に立っている。2位はIBM X-ForceのValentina Palmiotti氏で7万ドルを獲得した。

## Windows 11への攻撃と他の成果

Windows 11は初日だけで3チームによる権限昇格に成功した。AngelboyとTwinkleStar03（DEVCORE）がそれぞれ3万ドルを獲得し、独立したルートでヒープベースのバッファオーバーフローやUse-After-Free、アクセス制御の不備を利用した攻撃も実証された。Marcin Wiązowski氏とGMOサイバーセキュリティの河根謙太郎氏もそれぞれ3万ドルを獲得した。IBM X-ForceのPalmiotti氏はNVIDIA Container Toolkitに対するエクスプロイトで5万ドル、Red Hat Linux for Workstationsで2万ドルを獲得した。NVIDIA Megatron Bridgeに対してはSatoki Tsuji氏とhaehae氏がそれぞれ2万ドルを獲得し、過剰に許可されたアローリストとパストラバーサルの欠陥を突いた。

## AI製品が新たな主要標的に

今大会の特徴として、AIゲートウェイやAI開発ツールが重要なカテゴリとして設けられた点が挙げられる。LiteLLM（AIゲートウェイ）はk3vg3n氏がSSRF（サーバーサイドリクエストフォージェリ）とコードインジェクションを組み合わせたフルチェーン攻撃で4万ドルを獲得し、AIインフラへのシステム完全制御を実証した。OpenAI Codexに対しては2チーム（Compass SecurityとDoyensecのmaitai氏）がそれぞれ4万ドルを獲得した。LM StudioはSTARLabs SGが4万ドルを得た。Chromaデータベースもhaehae氏が攻略し2万ドルを獲得している。AIサービスの急速な普及を反映し、脆弱性研究の対象が従来のOSやブラウザから生成AIインフラへと拡大していることを示す結果となった。

## 今後の影響

発見されたゼロデイ脆弱性はイベント終了後、TrendMicroのZero Day Initiativeを通じてベンダーに通知され、ベンダーは90日以内にパッチを提供する必要がある。Pwn2Own Berlin 2026は5月16日まで3日間にわたって開催されており、残る2日間でさらなる脆弱性実証が行われる見込みだ。初日の成果は、エンタープライズ環境で広く使われるOSやブラウザだけでなく、急速に採用が進むAIツール・ゲートウェイにも深刻なゼロデイリスクが存在することを改めて浮き彫りにした。
