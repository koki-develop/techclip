---
date: "2026-08-11T20:14:06+09:00"
title: "Red Hat ACMにCVSS 9.9の重大脆弱性、名前空間編集権限だけでクラスタ管理者に昇格可能"
description: "Red Hat Advanced Cluster ManagementにCVSS 9.9の権限昇格脆弱性CVE-2026-10090が発見され、名前空間スコープの編集権限しか持たないユーザーが悪意あるHelmリポジトリ経由でKubernetesクラスタの完全な管理者権限を奪取できる状態にある。"
tags:
  - Security
  - Cloud
references:
  - "https://cyberpress.org/red-hat-acm-flaw-namespace-editors-escalate/"
  - "https://cybersecuritynews.com/red-hat-acm-privilege-escalation-vulnerability/"
  - "https://gbhackers.com/red-hat-kubernetes-flaw/"
---

## 概要

Red Hat Advanced Cluster Management for Kubernetes(ACM)に、CVSSスコア9.9(最高レベル)という極めて深刻な権限昇格の脆弱性CVE-2026-10090が発見された。この脆弱性の危険性は、必要とされる権限の低さにある。攻撃者は名前空間スコープの「編集」権限さえ持っていれば、クラスタ全体の管理者権限であるcluster-adminロールにまで昇格できてしまう。マルチテナント環境で複数のチームやユーザーに限定的な権限を委譲しているKubernetesクラスタにとって、テナント分離の前提そのものを覆しかねない問題であり、ACMを本番環境で運用する組織は早急な対応が求められる。

## 攻撃の仕組み

この脆弱性は「confused deputy(混乱した代理人)」問題として分類される。ACMのApplication Subscriptionコントローラーが、本来は低権限のユーザーが直接実行できない操作を、コントローラー自身の昇格された権限で代行してしまうことが根本原因だ。具体的な攻撃手順は次の通りとなる。まず、名前空間スコープの編集権限を持つ攻撃者が、自身の管理下にある悪意あるHelmリポジトリを指し示す「Channel」オブジェクトを作成する。次に、その悪意あるChannelを参照する「Subscription」オブジェクトを作成すると、脆弱なコントローラーが本来ユーザーには許可されていない昇格権限を用いて、指定されたHelmチャートを自動的にデプロイしてしまう。このチャートの中にClusterRoleBindingリソースを仕込んでおけば、任意のServiceAccountにcluster-adminロールを付与でき、結果としてクラスタ全体を掌握できる。CVSSベクトルは「AV:N/AC:L/PR:L/UI:N/S:C/C:H/I:H/A:H」で示される通り、攻撃元区分はネットワーク経由、攻撃条件の複雑さは低く、ユーザーの関与も不要という、悪用が容易な条件が揃っている。

## 影響範囲と対応状況

脆弱性が存在するのは、Red Hat Advanced Cluster Management for Kubernetes 2に含まれる「rhacm2/multicluster-operators-subscription-rhel9」コンポーネントである。ACMはマルチクラスタ環境の統合管理を担う中核コンポーネントであるため、影響を受けるとクラスタ単体にとどまらず管理下の複数クラスタ全体に波及するリスクがある。特に懸念されるのは、報道時点でRed Hatが「現時点でRed Hatの製品セキュリティ基準を満たす緩和策が存在しない("no mitigation currently meets its product-security criteria")」と明言している点で、正式な修正パッチはまだ提供されていない。

## 推奨される暫定対策

パッチが提供されるまでの間、Red Hatおよびセキュリティ研究者は以下の暫定対策を推奨している。まず、RBAC設定を見直し、必要最小限の権限のみを付与する最小権限の原則を徹底すること。特にChannelおよびSubscriptionオブジェクトを作成できるユーザーやグループを厳格に制限することが重要となる。あわせて、参照を許可するHelmリポジトリの所有権や出所を確認し、信頼できないリポジトリを指すChannelの作成を防ぐこと。さらに、ClusterRoleBindingの作成など、クラスタスコープのリソースに対する変更を継続的に監視し、異常なロール付与を早期に検知できる体制を整えることが望ましい。ACMを利用する組織は、Red Hatからの正式なセキュリティアドバイザリおよびパッチ提供状況を注視し、公開され次第速やかに適用する必要がある。
