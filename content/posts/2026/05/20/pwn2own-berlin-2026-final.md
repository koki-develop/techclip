---
date: "2026-05-20T02:49:44+09:00"
title: "Pwn2Own Berlin 2026閉幕：47件のゼロデイで総額130万ドル、DEVCOREがMaster of Pwn獲得"
description: "Pwn2Own Berlin 2026が3日間の開催を終え、47件のゼロデイ脆弱性の悪用に対して総額1,298,250ドルの賞金が授与され、DEVCOREがMaster of Pwn称号を獲得した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/hackers-earn-1-298-250-for-47-zero-days-at-pwn2own-berlin-2026/"
  - "https://securityaffairs.com/192250/hacking/pwn2own-berlin-2026-day-three-devcore-crowned-master-of-pwn-1-298-million-total.html"
  - "https://www.thezdi.com/blog/2026/5/16/pwn2own-berlin-2026-day-three-results-and-master-of-pwn"
---

## 大会概要と最終成績

セキュリティ研究者の腕を競う国際的なハッキングコンテスト「Pwn2Own Berlin 2026」が5月14〜16日の3日間にわたって開催された。世界中のセキュリティ研究者・チームが参加し、47件のユニークなゼロデイ脆弱性を悪用して総額**1,298,250ドル**（昨年比約20%増）の賞金を獲得した。

最終的なMaster of Pwn（総合優勝）には台湾のセキュリティ企業**DEVCORE**が輝いた。DEVCOREは50.5ポイントと505,000ドルを獲得し、2位のSTARLabs SG（25ポイント、242,500ドル）、3位のOut Of Bounds（12.75ポイント、95,750ドル）を大きく引き離した。初日から主導権を握ったDEVCOREは最終日も安定した成果を維持し、圧倒的な強さを見せた。

## 注目の攻撃成果

今大会で最高額の賞金を獲得した攻撃のひとつは、Orange TsaiことCheng-Da Tsai（DEVCORE所属）による**Microsoft Exchangeへの攻撃**だ。3つのバグを連鎖させることでSYSTEM権限でのリモートコード実行（RCE）を達成し、200,000ドルを獲得した。複数のバグを組み合わせる「バグチェーン」戦術は今大会全体を通じて多くのチームが採用した手法でもある。

同じく200,000ドルを獲得したのはSTARLabs SGのNguyen Hoang Thachで、**VMware ESXi**に対してメモリ破壊脆弱性を利用したクロステナントのコード実行を成功させた。DEVCOREのsplitlineは**Microsoft SharePoint**に対して2つのバグを連鎖させ100,000ドルと10ポイントを獲得。そのほか、**Windows 11**や**Red Hat Enterprise Linux**も複数チームから攻撃を受けた。

今大会で特筆すべき点として、**AIコーディングエージェントへの攻撃**が挙げられる。OpenAI Codexは3つの独立したチームによって異なる手法で攻略され、Anthropic Claude Codeも攻撃対象となった。LLMカテゴリーが正式な競技対象に加わったことで、AIシステムのセキュリティリスクが広く実証された形となった。

## 攻撃手法と今後の対応

3日間で確認された主な攻撃手法には、整数オーバーフローを利用した権限昇格、Use-After-Free（解放後使用）メモリ脆弱性、未初期化メモリの悪用、外部からの制御フロー操作などが含まれる。複数の脆弱性を組み合わせるバグチェーン戦術は高難度ターゲットの攻略において特に有効であることが改めて示された。

日程別の賞金額は初日が523,000ドル（24件）、2日目が385,750ドル（15件）、3日目が389,500ドル（8件）で、初日に最も多くのゼロデイが集中した。今大会で発見・実証されたすべての脆弱性は、Zero Day Initiativeの慣例に従い各ベンダーへ通知済みで、**90日間の開示猶予期間**内にパッチの提供が求められる。エンタープライズ製品からAIシステムまで広範なターゲットでゼロデイが次々と発見された今大会の結果は、業界全体のセキュリティ強化に向けた重要な知見となる。