---
date: "2026-07-26T02:24:05+09:00"
title: "Azure West USで5時間の通信障害、メンテナンス時のIPルート誤削除が原因と判明"
description: "Microsoft Azure West USリージョンで発生した約5時間の障害について、Microsoftはルーティンメンテナンス中の自動システムによるIPルート誤削除が原因だったと説明した。"
tags:
  - Cloud
references:
  - "https://www.datacenterdynamics.com/en/news/microsoft-azure-outage-at-west-us-region-causes-intermittent-connectivity-failures/"
  - "https://www.networkworld.com/article/4201168/microsoft-explains-why-its-west-us-azure-and-cloud-services-failed.html"
---

## 概要

2026年7月23日、Microsoft AzureのWest USリージョンでApp Service、Azure Kubernetes Service (AKS)、Cosmos DB、Teams・Outlookなどの Microsoft 365 関連サービスを含む20以上のサービスに影響する通信障害が発生した。障害はUTC 14:44から19:41まで(太平洋時間で午前7:44から午後12:41まで)の約5時間にわたって続き、断続的な接続障害としてユーザーに影響を与えた。Microsoftは事後説明で、原因はルーティンのメンテナンス作業中にIPルートが誤って削除されたことにあったと明らかにした。

## 障害の原因

Microsoftの説明によれば、定期メンテナンス作業の一環でデバイスを隔離する過程で、自動化システムが本来の対象に含まれていなかった追加のデバイスを隔離対象に含めてしまった。その結果、事前の影響評価の対象になっていなかったIPルートまでもが誤って削除され、West USリージョンの施設への出入りトラフィックが遮断される事態となった。一方で、West USリージョン内で完結して動作していたサービスについては影響を受けなかったとされており、障害は地域外との通信経路に限定された形だった。

## Microsoftの対応

Microsoftのエンジニアチームは障害発生から1時間以内に問題を特定し、サービス復旧の作業に着手した。最終的に約5時間後に通信は正常化した。Microsoftは再発防止に向けて、単一リージョンへの依存を減らす「マルチリージョンアプローチ」の採用を顧客に推奨している。

## 背景と今後の展望

今回の障害は、Microsoftにとって今年2度目となる大規模なクラウド障害である。2026年2月には米国東部・西部リージョンにまたがる約10時間に及ぶ障害が発生しており、大手クラウドベンダーの単一障害点がビジネスに与える影響の大きさが改めて浮き彫りになった。Azureは企業向けサービスの基盤として広く利用されているだけに、今後もインフラの冗長化や自動化システムの安全策の強化が課題として注目される。
