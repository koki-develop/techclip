---
date: "2026-08-31T18:18:29+09:00"
title: "Carharttのデータ侵害、実被害は1290万件でShinyHuntersの当初主張の半分と判明"
description: "アパレル大手CarharttがShinyHuntersによるDatabricks経由のデータ侵害を受け、Troy Huntの検証で実際の被害は当初発表の約半分となる1290万件と確認された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/carhartt-data-breach-exposes-information-of-129-million-accounts/"
  - "https://www.theregister.com/security/2026/08/26/carhartt-data-breach-affects-129m-half-of-what-shinyhunters-claimed/5292626"
---

## 概要

米アパレル大手Carharttが、ハッキング集団ShinyHuntersによるデータ侵害の被害に遭った。ShinyHuntersはCarharttのDatabricks分析基盤に不正アクセスし、約50GBの顧客・従業員データを窃取。8月13日、330万ドルの身代金要求にCarharttが応じなかったことを受け、盗んだデータを公開した。当初ShinyHuntersは2500万〜2600万件規模の情報流出を主張していたが、セキュリティ研究者Troy Huntの検証により、実際に正当なデータと確認できたのは1290万件、当初主張のおよそ半分にとどまることが判明した。

## 侵害の経緯と手口

ShinyHuntersはCarharttのクラウドベースのデータ基盤「Databricks」を経由して侵入した。Databricksは業務レポーティングとデータストレージを統合したプラットフォームで、近年SaaSやクラウドインフラの脆弱性を突く同グループの標的の一つとなっている。窃取されたデータには氏名・メールアドレス・電話番号・物理住所に加え、@carhartt.comドメインの従業員アカウント1万5000件超の認証情報、ロイヤリティ情報を含む顧客メタデータ、企業文書も含まれていた。ShinyHuntersはCarharttに330万ドルを要求したが、Carharttは「経営陣との協議の結果、交渉には応じない」と回答し拒否。これに対しShinyHuntersは交渉担当者を「未熟で無能」と評するなど反発し、8月13日にデータを公開した。

## Troy Huntによる検証で判明した水増し

ShinyHuntersは当初、約2500万〜2600万件のアカウント情報を窃取したと主張していたが、Have I Been Pwned運営者のTroy Huntが独自に検証した結果、実際の被害規模はその半分の1290万件にとどまることが分かった。Huntはまずオープンソースのメール抽出ツールで約2500万件のメールアドレスを抽出。次にAI分析ツール「OpenClaw」で異常検知を行い、人手によるレビューも加えた多層的な手法で精査した。その結果、"lkvb06fkzsjv.org"のようなランダムな文字列ドメイン（TPC-DSテストデータセットに典型的なパターン）、小売企業としては不自然なほど.eduや.orgドメインが集中している点、米国よりもモンテネグロ在住者が多いという地理的分布の不自然さ、生年月日が1900年代初頭に偏っている点など、合成データ特有の特徴が多数見つかった。OpenClawによる分析だけでも、当初の2480万件から1360万件へと推定値が引き下げられている。

## 実被害の内容と今後の影響

最終的にHuntが正当なデータと確認したのは、氏名・メールアドレス・電話番号・物理住所を含む1290万件のアカウント情報だった。Have I Been Pwned側の分析では、これらアカウントの83%が過去の他の侵害データベースにも登録済みであることが指摘されており、完全に新規の情報漏洩というよりも既存の流出データと重複する部分が大きいとみられる。Carharttはこの件について、Huntの検証結果を含めて公式なコメントを出していない。ShinyHuntersはこれまでもGoogle、Cisco、Match Group、Rockstar Games、医療機器メーカーのMedtronicなどSaaS・クラウド基盤の脆弱性を突く形で大手組織を標的にしており、Databricksのような分析基盤が新たな攻撃経路として狙われ続けている実態が改めて浮き彫りになった。
