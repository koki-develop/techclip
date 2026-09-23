---
date: "2026-09-24T08:09:47+09:00"
title: "ShinyHunters、FBI侵入とTB級データ窃取を主張——PeopleSoftゼロデイと報復動機"
description: "恐喝集団ShinyHuntersがOracle PeopleSoftのゼロデイ脆弱性を悪用してFBIに侵入し、捜査官や採用応募者に関する2〜3TB相当の個人情報を窃取したと主張、FBIは調査を認めている。"
tags:
  - Security
references:
  - "https://techcrunch.com/2026/09/22/hacking-group-shinyhunters-claims-it-breached-the-fbi-stole-agents-and-applicants-data/"
  - "https://www.bleepingcomputer.com/news/security/shinyhunters-claims-fbi-hack-data-theft-in-peoplesoft-zero-day-breach/"
  - "https://thehackernews.com/2026/09/shinyhunters-claims-fbi-breach-says-it.html"
---

## 概要

恐喝集団ShinyHuntersは、Oracle PeopleSoftのゼロデイ脆弱性を悪用してFBIのシステムに侵入し、捜査官や採用応募者に関する機密個人情報を大量に窃取したと主張している。窃取量は2〜3テラバイトに及ぶとされ、氏名・自宅住所・電話番号・配偶者情報に加え、人事部門や医療部門(Medlink)が保有する健康情報まで含まれるという。FBIの採用サイト「FBIjobs.gov」は攻撃者による改ざんの被害に遭い、一時「メンテナンス中」の表示に切り替わった。FBIは「FBIjobs.govに対する不正行為の疑いを認識しており、現在調査中」とコメントしているが、詳細な確認や被害範囲の公表には至っていない。

## 侵入の手口とゼロデイ脆弱性

ShinyHuntersの主張によれば、攻撃は月曜夜にOracle PeopleSoftの認証前リモートコード実行(RCE)を可能にする未公開のゼロデイ脆弱性を突く形で始まり、まず採用応募者情報を保管するPeopleSoftサーバーへ侵入した後、Amazonが提供するFBI管理下のGovCloudインフラへ横展開(ラテラルムーブメント)したとされる。同グループは同じ脆弱性を悪用してフォーチュン500企業を含む他の組織も標的にしていると主張しており、これは2026年6月に恐喝活動で悪用したPeopleSoftの既知の脆弱性(CVE-2026-35273)とは別の未公開の欠陥だとされる。ただしBleepingComputerは、ゼロデイの実在性やラテラルムーブメントの経路、窃取データ量について独立した検証はできていないと明記しており、404 Mediaが盗まれたとされるサンプル記録の一部について真正性を確認したにとどまる。

## 動機は報復か

ShinyHuntersは今回の侵入について金銭目的ではないと主張し、2026年5月にFBIが公表したFLASHレポート(オンライン学習管理システム「Canvas」を標的とした同グループの手口を詳述し、身代金支払いに応じないよう警告した公式声明)への報復だと説明している。同グループは、このレポートが自分たちの脅迫行為を「誇張した虚偽の主張」で描いていると反発し、1週間以内に内容の修正・撤回を行うよう要求しているが、応じなかった場合にどうするかについては「ノーコメント」として明言を避けている。この経緯は、法執行機関の公式発表を逆手に取って攻撃対象を選ぶという、サイバー犯罪集団側の新しい報復パターンを示す事例といえる。

## FBIの対応と専門家の見方

FBIは侵害の発生自体を否定していないものの、公式コメントは調査継続を認めるにとどまっている。ShinyHunters側は、侵入を検知したFBIが直ちに関連システムをシャットダウンしたと述べている。Cato NetworksのEtay Maor氏は、「ShinyHuntersによるFBI侵害の主張は、法執行機関とサイバー犯罪集団の対立の中でも異例に挑発的な動きであり、真剣に受け止めるべきだ」と指摘する。仮に主張通りの情報が流出していれば、外国政府がFBI職員やその家族を標的に脅迫・強要工作を仕掛ける「重大な防諜上の脅威」になりかねないとの懸念も出ている。今回の一件は2026年に入って判明したFBI関連の侵害としては2件目であり、法執行機関を狙う恐喝集団の攻撃対象としての「格上げ」を印象づける事案となっている。
