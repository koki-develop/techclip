---
date: "2026-08-25T14:09:24+09:00"
title: "AWS、ラスベガスに新Local Zoneを一般提供開始、低遅延ワークロード向けにEC2・EKSなど対応"
description: "AWSがネバダ州ラスベガスに新しいLocal Zone「us-west-2-las-2a」を一般提供開始し、EC2やEKSなど主要サービスを1桁ミリ秒の低遅延で利用可能にした。"
tags:
  - Cloud
references:
  - "https://aws.amazon.com/about-aws/whats-new/2026/08/aws-local-zones-las-vegas-nevada/"
---

## 概要

AWSは2026年8月20日、米ネバダ州ラスベガスに新しいAWS Local Zone「us-west-2-las-2a」の一般提供を開始したと発表した。米国西部(オレゴン)リージョンに属するこのLocal Zoneにより、ラスベガス都市圏のユーザーは主要なAWSサービスを1桁ミリ秒台の低遅延で利用できるようになる。AWS Local Zonesは、コアとなるAWSサービスをリージョンの外にある大都市圏に拡張し、地理的に近い場所でコンピュートやストレージを提供する仕組みで、今回の開設により世界で30以上の大都市圏にLocal Zoneが展開されたことになる。

## 対応サービスとアクセス方法

新設のLocal Zoneでは、コンピュートとしてC7i、M7i、R7i、C8gnの各EC2インスタンスタイプ、ストレージとしてgp3、gp2、io1、sc1、st1のEBSボリュームタイプが利用可能となっている。コンテナサービスとしてはECSとEKSに対応し、ネットワーク関連ではApplication Load BalancerおよびAWS Direct Connectも利用できる。ユーザーはAWS Management ConsoleのAWS Global ViewにあるRegionsタブから該当Local Zoneを有効化するか、ModifyAvailabilityZoneGroup APIを利用して有効化できる。

## 想定される用途と背景

AWSはLocal Zonesの狙いとして、レイテンシーに敏感なアプリケーションの高速化、データレジデンシー要件への対応、AI/ML推論ワークロードの近接処理、そしてレガシーアプリケーションのクラウド移行支援を挙げている。ラスベガスは大規模なイベント産業やエンターテインメント施設が集積する都市であり、こうした現地拠点でのリアルタイム性が求められる用途に対して、リージョンをまたぐ通信よりも低遅延なインフラを提供できる点が今回の開設の意義といえる。

## 今後の展望

AWSはLocal Zonesの展開を継続的に拡大しており、既存の30以上の大都市圏に加えて今後も対象地域が増えていくとみられる。企業が特定の都市圏でエッジに近い形でAWSサービスを利用したいというニーズに応える形で、Local Zonesはハイブリッドクラウドやエッジコンピューティング戦略の選択肢の一つとして位置づけられている。
