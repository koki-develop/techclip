---
date: "2026-11-04T08:07:08+09:00"
title: "Microsoft、Azure Deployment EnvironmentsとDev Boxを代替製品なしで廃止へ"
description: "MicrosoftがAzure Deployment EnvironmentsとMicrosoft Dev Boxの提供終了を発表し、後継製品を出さずBicepやARMテンプレートへの移行を利用者に求めている。"
tags:
  - Cloud
references:
  - "https://www.infoq.com/news/2026/10/ade-dev-box-retirement/"
---

## 概要

Microsoftは、セルフサービス型のインフラ管理サービスであるAzure Deployment Environments(ADE)と、クラウドベースの開発環境を提供するMicrosoft Dev Boxの提供終了を発表した。ADEは2027年2月22日に、Dev Boxは2028年9月18日にそれぞれ終了する予定で、Dev Boxのシャットダウン期間は2026年9月14日から既に始まっている。両サービスとも後継となる代替製品は用意されず、Microsoftは利用者に対し、Azure Resource Manager(ARM)テンプレートやBicepを用いた直接のInfrastructure as Code(IaC)デプロイへの移行を推奨するガイダンスのみを提示している。

## 廃止の理由と移行先

Microsoftが示した説明は限定的なものだった。Dev Boxについては、投資をWindows 365へ再配分するためとされている。一方でDeployment Environmentsの終了に関しては、同等の説明は示されておらず、移行手順の案内のみが提供されている形だ。移行先としてMicrosoftが挙げているのは、ARMテンプレートやBicepによる直接デプロイ、環境プロビジョニングのためのCI/CDワークフローの構築、そして標準化されたコンポーネントとしてのAzure Verified Modulesの活用である。ただしMicrosoft自身も、サードパーティ製ソリューションのいずれも「BicepやARMのライフサイクルを直接サポートするものはない」と認めており、単純な置き換え先が存在しないことを示している。

## 利用者への影響

この廃止により、ADEやDev Boxが提供していたセルフサービス型のガバナンス機能は失われることになる。エンジニアのYoshizaki氏は「その価値が正しく認識されていなかった」と今回の決定を批判し、BicepなどのIaCツールだけでは、これらの製品が提供していたカタログ機能、ロール管理、開発者向けポータルといった機能を再現できない点を指摘している。利用チームは今後16か月の間に、既存の構成を棚卸しし、シナリオごとに代替手段を検証し、ワークロードを手作業で移行する必要に迫られる。廃止日を過ぎてなお移行が完了していないワークロードは削除され、復旧手段は提供されない見込みだ。

## 今後の見通し

今回の決定は、開発者向けのセルフサービス環境管理という分野において、Microsoftが自社製のマネージドサービスから手を引き、利用者自身がIaCやCI/CDの仕組みを組み合わせて運用する方向へ回帰する動きと言える。ガバナンスや開発者体験の面で機能的なギャップが残ることから、既存ユーザーにとっては移行コストと運用の複雑化が避けられない課題となりそうだ。
