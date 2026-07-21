---
date: "2026-07-22T02:33:21+09:00"
title: "ShinyHuntersが悪用したPeopleSoft認証前RCE、Oracleが過去最大級の7月定例パッチで修正"
description: "Oracleは2026年7月の四半期定例パッチでShinyHuntersが100以上の組織を侵害するために悪用したPeopleSoftの認証前RCE脆弱性を含む脆弱性を修正した。"
tags:
  - Security
references:
  - "https://www.techtimes.com/articles/321140/20260721/peoplesoft-exploit-behind-100-breaches-gets-patched-oracles-record-july-cpu.htm"
  - "https://threat-modeling.com/oracle-july-2026-critical-patch-update/"
---

## 概要

Oracleは2026年7月21日、四半期ごとの定例パッチ(Critical Patch Update、CPU)を公開した。今回のCPUは同社の企業向けオンプレミス製品全体で1,455件という過去最大級の脆弱性を一括修正するもので、その中には犯罪グループShinyHuntersが実際に悪用し、100以上の組織から約300台のサーバーを侵害するために使われたPeopleSoft PeopleToolsの認証前リモートコード実行(RCE)脆弱性が含まれる。CPU全体ではWebLogic Server、PeopleSoft、Identity Manager、WebCenter、WebCenter Capture、VirtualBoxにまたがり5件の緊急(CVSS 9.0以上)、12件以上の重要(High)脆弱性が対処された。

## ShinyHuntersによる悪用の経緯

Mandiant(Googleの脅威インテリジェンス部門)が追跡するUNC6240ことShinyHuntersは、2026年5月27日からPeopleSoft PeopleTools 8.61/8.62のUpdates Environment Managementコンポーネントに存在するCVE-2026-35273(CVSS 9.8)を未パッチのゼロデイとして悪用を開始した。この脆弱性は`/PSEMHUB/`エンドポイントに対する単一のHTTPリクエストのみで認証なしにサーバーを完全に乗っ取れるというもので、攻撃者はMeshCentralの改造版をMicrosoft Azureのサービスに偽装させて展開し、盗んだ認証情報をシェルスクリプトでSSH経由に展開、WebLogicディレクトリにJSP webshellを設置してデータを段階的に圧縮・窃取するという手口を用いた。

悪用は6月9日まで約2週間続き、Oracleが緊急のセキュリティ警告を発表したのは6月10日で、その間パッチは存在しなかった。この攻撃により100以上の組織、約300台の脆弱なインスタンスが侵害され、被害組織の68%が高等教育機関、特に米国の大学が中心だった。最も早く被害が確認されたノッティンガム大学では約40GB・45万5,000人分の学生・卒業生の個人情報や請求記録が流出し、Moody Bible Instituteでは230万件の個人記録が流出したと報告されている。Mandiant Consultingの最高技術責任者Charles Carmakalは、キャンペーンが依然として活動中であり、恐喝メッセージの送付が続いていることを確認したと述べている。

## 7月定例パッチの内容

今回のCPUで修正されたPeopleSoft関連の脆弱性はCVE-2026-35278(CVSS 9.8)で、これは認証不要・HTTPアクセスのみでPeopleSoftアプリケーションサーバーと基盤ホストを完全に侵害できるリモートコード実行の欠陥である。CPU全体としては、WebLogic Serverの認証不要T3/IIOP経由RCEであるCVE-2026-35263(CVSS 9.9)、Identity ManagerのHTTP経由RCEであるCVE-2026-35268(CVSS 9.9)、WebCenter SitesのCVE-2026-35270(CVSS 9.1)、WebCenter CaptureのCVE-2026-35280およびCVE-2026-35281(いずれもCVSS 9.9)が緊急レベルの脆弱性として修正された。重要度の高い脆弱性としては、認証済みRCEのCVE-2026-35259(WebLogic、CVSS 8.8)、権限昇格・RCEにつながるCVE-2026-35271(PeopleSoft+WebLogic、CVSS 8.7)、ゲスト・ツー・ホスト脱出のCVE-2026-35275(VirtualBox、CVSS 7.5)などが含まれる。

## 推奨される対応

セキュリティ専門家は、PeopleSoftおよびWebLogic環境へのパッチを72時間以内に適用することを強く推奨している。あわせて、Oracleミドルウェアをインターネットに直接公開しないネットワーク隔離、全Oracleアプリケーションサーバーでの詳細なアクセス・エラーログの有効化、パッチ適用後の管理者認証情報のリセット、PeopleSoftサーバーにおける不審なプロセスや設定変更の侵害調査が求められる。Oracleはパッチが存在しなかった期間の緩和策として、複数サーバー環境ではEnvironment Management Hubサービスの無効化、単一サーバー環境では`/PSEMHUB/*`と`/PSIGW/HttpListeningConnector`への外部アクセス遮断を案内していたが、今回のCPUで恒久的な修正が提供されたことになる。ShinyHuntersによる恐喝キャンペーンは本稿執筆時点でも継続しているとされ、被害組織や関連組織は侵害の有無を改めて確認する必要がある。
