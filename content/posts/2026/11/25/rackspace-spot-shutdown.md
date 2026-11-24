---
date: "2026-11-25T08:07:06+09:00"
title: "Rackspace、Kubernetesシークレット窃取の侵害受けクラウド基盤「Spot」を12月8日に終了"
description: "RackspaceはKubernetesクラスタの認証情報が窃取される侵害を受け、クラウドプラットフォーム「Spot」を12月8日に完全終了すると発表した。"
tags:
  - Cloud
  - Security
references:
  - "https://www.scworld.com/brief/rackspace-discloses-security-breach-of-spot-cloud-platform"
  - "https://www.bleepingcomputer.com/news/security/rackspace-shuts-down-spot-cloud-platform-after-security-breach/"
---

## 概要

Rackspaceは、同社のKubernetesベースのクラウドプラットフォーム「Spot」が不正アクセスを受けたことを受け、サービス自体を終了すると発表した。11月17日に漏洩した認証情報を使った攻撃者による不正アクセスが発生し、顧客からの報告を受けて11月18日に侵入が発覚した(同社は念のため11月16日以降のアクセスログも確認するよう顧客に推奨している)。同社は一時的にサービスを停止して対応に当たり、11月21日に復旧させていたが、最終的に顧客に12月8日午後5時(中部時間)までの移行を求め、Spot自体を閉鎖するという判断を下した。

## 侵害の内容

攻撃者は窃取した認証情報を使い、顧客のKubernetesクラスタ内で不正なPodを作成し、Secret(機密情報)の読み取りや、ノード・ボリュームの一覧取得が可能な状態にあった。これにより、APIトークン、リフレッシュトークン、kubeconfig、Kubernetes Secretが窃取された可能性があるとして、Rackspaceは顧客にこれらすべてを侵害済みとみなして対処するよう求めている。同社は、侵害を受けた環境は中核インフラとは分離されており、他の顧客環境への影響を示す証拠はないとしている。

## サービス終了とその影響

Rackspaceは侵害対応と並行してSpotプラットフォーム自体の終了を決定し、顧客に対し12月8日の期限までにデータの取得とワークロードの移行を完了するよう要請した。期限を過ぎると、残存するワークロードはすべて停止され、顧客データへのアクセスもできなくなるという。Spotはコンテナ化されたアプリケーションをKubernetes技術で展開・管理できる低価格のクラウド基盤として利用されており、Reddit上では低コストを評価する一部ユーザーから、値上げしてでもサービス継続を望む声も上がっている。もっとも、Kubernetesの認証情報そのものが攻撃対象となった点は、同種のマネージドKubernetesサービスを提供する他事業者にとっても教訓となりそうだ。
