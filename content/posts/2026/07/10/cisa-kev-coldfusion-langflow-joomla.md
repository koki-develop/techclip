---
date: "2026-07-10T02:41:08+09:00"
title: "CISA、Adobe ColdFusionやLangflowなど実悪用中の脆弱性4件をKEVに追加、連邦機関に7月10日までの緊急パッチ適用を義務化"
description: "CISAはAdobe ColdFusion、Joomla拡張機能2件、LangflowのCVSS最大10.0の脆弱性4件を実際に悪用されているとしてKEVカタログに追加し、連邦機関に7月10日までのパッチ適用を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/07/cisa-adds-4-actively-exploited-adobe.html"
  - "https://www.securityweek.com/cisa-urges-immediate-patching-of-exploited-coldfusion-langflow-joomla-flaws/"
  - "https://www.scworld.com/news/cisa-adds-coldfusion-langflow-and-two-joomla-bugs-to-known-exploited-vulnerabilities-list"
---

## 概要

米サイバーセキュリティ・インフラセキュリティ庁(CISA)は2026年7月7日、実際に悪用が確認されている4件の脆弱性を「既知の悪用された脆弱性(KEV)」カタログに追加し、連邦政府機関に対して7月10日までのパッチ適用を義務付けた。対象はAdobe ColdFusion、Joomlaの拡張機能2件(SP Page BuilderおよびPage Builder CK)、そしてAI駆動のワークフローツールLangflowで、いずれもすでに攻撃者による悪用の痕跡が観測されている。

## 脆弱性の詳細

最も深刻なのはAdobe ColdFusionのパストラバーサル脆弱性(CVE-2026-48282、CVSS 10.0)で、リモート開発サービス(RDS)のファイル/IOハンドラーの欠陥を突き、認証なしの単一HTTPリクエストでウェブシェルを直接書き込める。6月30日のパッチリリースからわずか数時間後にインドのIPアドレス(103.207.14[.]220)からの悪用が記録されており、Suzu LabsのDenis Calderone氏は「RDSが有効化されている環境に限られる」と条件を付けつつも、攻撃開始までの速さを問題視している。

Joomlaでは2つの拡張機能が標的となった。Page Builder CK(CVE-2026-56290、CVSS 10.0)はアクセス制御不備により未認証での任意ファイルアップロードが可能で、6月27日以降ウェブシェル配信に悪用されており、バージョン3.6.0で修正済みだ。JoomShaperのSP Page Builder(CVE-2026-48908、CVSS 10.0)は危険なファイルタイプの無制限アップロードを許し、未認証ユーザーがPHPコードを実行できる。攻撃者は隠れた管理者アカウントを作成し、PHPファイルマネージャー型のバックドアを配備していることが報告されており、バージョン6.6.2以降へのアップデートが推奨されている。

LangflowのCVE-2026-55255は、NVDによればCVSS 3.1で8.4(HIGH)とされる認可バイパス(IDOR)の脆弱性で、`/api/v1/responses`エンドポイントにおいて認証済み攻撃者が他ユーザーのフローIDを指定することで、そのユーザーのフローを実行できてしまう。バージョン1.9.1で修正済みだが、報道によってはCVSSスコアが6.1や9.9と記載されるなど情報源間でばらつきが見られる。

## Langflowを標的とした悪用キャンペーン

セキュリティ企業Sysdigは6月26日、Langflowを狙った持続的な攻撃キャンペーンについて警告を発した。単一のオペレータ(IPアドレス45.207.216[.]55)が6月22日から25日にかけて、ホスト偵察とフローID収集を経てCVE-2026-55255のIDORを悪用し、他テナントのLLMプロバイダーAPIキーやAWSキーを窃取。さらに別のリモートコード実行の脆弱性であるCVE-2026-33017と組み合わせることで、二段階のダウンローダーペイロードを展開していたことが確認された。専門家はボットネット構築や暗号通貨マイニングを目的とした金銭動機の攻撃である可能性を指摘する一方、AI基盤を標的とした攻撃の増加を懸念する声もあり、一部ではJADEPUFFERランサムウェア事件との関連にも言及されている。

## 今後の対応と専門家の見解

連邦機関は連邦民間行政機関(FCEB)向けの拘束的運用指令(BOD 26-04)に基づき、7月10日までに4件すべてへの対応が求められる。HadrianのMatan Shavit氏は「CVSSスコアだけで深刻度を判断するのではなく、システムが実際にどれだけ公開されているか、認証要件がどうなっているかという文脈を踏まえて優先順位を決めるべきだ」と指摘しており、企業や組織にも同様の観点からの迅速な対応が求められている。
