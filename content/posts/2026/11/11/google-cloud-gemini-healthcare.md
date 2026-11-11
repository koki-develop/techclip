---
date: "2026-11-11T18:09:40+09:00"
title: "Google Cloud、EpicやOracle Healthと連携する医療向けエージェントAI「Gemini for Healthcare」を発表"
description: "Google Cloudが電子カルテや請求システムを横断統合する医療向けAI「Gemini for Healthcare」を発表、HCA HealthcareやStanford医学部など7機関が初期導入パートナーとして参加する。"
tags:
  - Cloud
  - AI
references:
  - "https://www.googlecloudpresscorner.com/2026-11-10-Google-Cloud-Launches-Gemini-for-Healthcare"
---

## 概要

Google Cloudは11月10日、電子カルテ(EHR)や請求システム、臨床ガイドラインを横断的に統合し、複雑な臨床・行政ワークフローを自動化するエージェント型AIソリューション「Gemini for Healthcare」を発表した。主要なEHRベンダーであるEpic(open.epic API経由)やOracle Health(FHIR API経由)と連携するほか、NextGen Healthcareへの対応も数ヶ月以内に追加予定で、InterSystems FHIR Serverによる標準化データ管理や、400以上の医療アプリケーションに対応するKeragonとの連携も組み込む。初期導入パートナーにはBlue Cross Blue Shield of Massachusetts、Hartford HealthCare、HCA Healthcare、Highmark Health、Northwell Health、Optum、Stanford School of Medicineの7機関が名を連ねており、医療現場でのAIエージェント活用を本格的に推進する狙いがある。

## 主な機能とユースケース

Gemini for Healthcareは、複数のEHRに分散した患者データ・処方・検査結果を統合して提示する「医療記録統合」、Optum Network Eligibilityなどと連携した事前承認・保険カバレッジ確認、Sukiの環境音声知能を活用した臨床文書作成の自動化、GoodRxやWaystarと連携した処方価格・保険確認を含む請求処理の自動化など、幅広いユースケースをカバーする。背景には、米国の臨床医が週28時間を文書作成に費やし、医師の41.9%がバーンアウト状態にあるという実態、さらに医療機関の行政コストが医療支出全体の25〜35%を占めるという構造的な課題があり、データの断片化と現場職員の負担軽減が急務とされてきた。

## 技術基盤と導入パートナーの声

技術的には、GoogleとAnthropic、OpenAIの各モデルをサポートし、定型業務は低コストな軽量モデルへ、複雑な分析は推論力を強化したモデルへ自動的に振り分ける「スマートルーティング」を採用する。顧客データはHIPAA準拠の独立したエンタープライズ環境で管理され、引用可能な検証済み情報源に基づく回答により監査可能性を確保する設計だ。PHI(保護対象保健情報)の保護にはCheck PointやCyeraがセキュリティパートナーとして関わる。導入パートナーからは期待の声が上がっており、Hartford HealthCareのJoel Vengco氏は「患者情報を安全かつ責任を持って合成できれば、患者情報をより迅速に理解できる」と述べ、HCA HealthcareのMichael Schlosser医学博士も「複数のEHRシステムに分散した患者情報を解釈・合成し、より完全で一貫性のある病歴理解を支援する」とコメントしている。Stanford医学部のTodd Ferris氏は、研究者がSQLの知識なしに平易な言葉で質問できるようになり、データアナリストの作業時間削減につながると評価した。

## 今後の展開

Google Cloudは今後数ヶ月以内にNextGen Healthcareへの対応を追加するほか、Accenture、Deloitte、PwCといった医療システムインテグレーターとの協業により導入を加速させる方針だ。また、Google Cloud Marketplace上では複数のデジタルヘルス企業が追加のエージェント開発を進めており、今回の7機関に続く導入拡大とエコシステムの広がりが見込まれる。
