---
date: "2026-10-21T08:10:05+09:00"
title: "Google Cloudロンドン拠点で電源障害、HSBCやLloydsなど英国の金融・物流サービスに連鎖的影響"
description: "Google Cloudの英ロンドンリージョンの1ゾーンで電源障害が発生し、BigQueryやCloud Runなど約38サービスが停止、HSBCやLloyds Bank、Royal Mailなど英国の主要サービスが広範囲に影響を受けた。"
tags:
  - Cloud
references:
  - "https://www.theregister.com/paas-and-iaas/2026/10/20/google-clouds-london-zones-takes-a-nap-multiple-services-disrupted/5304084"
  - "https://www.theregister.com/paas-and-iaas/2026/10/20/google-cloud-says-a-power-event-caused-todays-outage/5304160"
---

## 概要

Google Cloudの英ロンドンリージョン(europe-west2)のゾーンの一つであるeurope-west2-bで、10月20日午前6時8分(UTC)頃から電源障害が発生し、BigQuery Data Transfer Service、Cloud Filestore、Cloud Run、App Engine、Cloud NetApp Volumes、Google Kubernetes Engine(GKE)、Managed Service for Apache Kafkaなど、専門家の分析によれば約38のサービスに影響が及んだ。Googleは当初「europe-west2リージョンで複数のGoogle Cloudサービスにエラー増加と断続的なネットワーク障害が発生している」と説明し、その後原因を「電源イベント」によるものと公表した。影響はクラウド基盤の裏側だけに留まらず、Lloyds Bank、HSBC、Revolutといった金融機関から、Royal Mail、DPD、BT、Rightmove、Screwfixまで、英国の金融・物流・公共サービスを広く巻き込む事態となった。NHS関連サービスへの影響も報じられている。

## 障害の経緯と対応

Googleは当初、復旧の見通しを示せず、ワークアラウンドについても「現時点では特になし」としたうえで午前9時30分(UTC)頃に状況を更新すると説明した。その後、午前10時18分(UTC)の更新で、顧客に対しワークロードを別の利用可能なロケーションへ移行するよう案内した。その後、午前11時58分(UTC)に午後1時(UTC)頃までの暫定復旧見込みを発表し、午後2時3分(UTC)にはほとんどの顧客向けにサービスが復旧、午後5時37分(UTC)の更新では大多数について障害が緩和され、残存する影響は軽微であるとされた。Googleは最終的に「電源イベントがeurope-west2-bゾーン内で障害を引き起こし、その電源イベントは緩和された」と総括している。なお、europe-west2リージョンは3つのゾーンで構成されており、Google Studioなど一部サービスは影響を受けなかった。障害発生中、Revolutは「すべての顧客の資金とデータは安全だ」と顧客に向けて説明した。

## 単一ゾーン障害がもたらす連鎖的インパクト

今回の事案が注目されるのは、単一のアベイラビリティゾーンの電源障害という比較的限定的な事象が、銀行の決済から郵便の配送追跡、不動産情報サイト、通信事業者まで、国レベルで広範な業務停止を引き起こした点にある。Keele大学のコンピュータサイエンス講師であるAmro Al-Said Ahmad氏は、現代のクラウド生態系に特有の「依存関係の効果」が、中核インフラの一部に障害が起きた際に連鎖的な障害(cascading failures)を誘発しやすい構造を指摘している。マルチクラウドやマルチリージョン構成を取らず、単一ゾーンへの依存度が高い企業ほど影響を受けやすかったとみられ、今回の障害は重要インフラを支える企業に対し、冗長性設計の見直しを迫る出来事となりそうだ。
