---
date: "2026-03-29"
title: "ゲームサーバーOSS「Agones」がCNCF Sandboxプロジェクトに、Google・Ubisoftが育てたKubernetesベースの基盤がコミュニティ主導へ"
description: "GoogleがKubernetes上のマルチプレイヤーゲームサーバー管理プラットフォーム「Agones」をCNCFにSandboxプロジェクトとして寄贈し、ベンダー中立なコミュニティ主導のガバナンス体制へ移行した。"
tags:
  - Cloud
  - OSS
references:
  - "https://www.cncf.io/blog/2026/03/23/agones-moves-to-the-cncf-a-new-era-for-open-source-multiplayer-game-infrastructure/"
---

## 概要

Googleは2026年3月、Kubernetes上でマルチプレイヤーゲームの専用サーバーをオーケストレーション・スケーリングするオープンソースプラットフォーム「Agones」を、Cloud Native Computing Foundation（CNCF）にSandboxレベルのプロジェクトとして寄贈した。これにより、Agonesはベンダー中立なコミュニティ主導のガバナンス体制へと移行し、Google以外のクラウド事業者やゲームスタジオからの参加拡大が期待される。

Agonesは2017年にGoogleとUbisoftの共同開発で誕生し、現在は250人以上のコントリビューターによって支えられている。プロジェクト創設者でリードメンテナーのMark Mandel氏は「マルチプレイヤーゲームサーバーのホスティングはかつて独自のプロプライエタリシステムに完全に依存していたが、オープンソースがゲームを変えた」と語り、CNCF移管の意義を強調した。

## 技術的な特徴

Agonesの最大の強みは、Kubernetesを拡張してゲームサーバーのライフサイクル管理を標準化する点にある。PC、コンソール、モバイルといったプラットフォームを問わず、一度ビルドしたサーバーバイナリを修正することなく、オンプレミスを含む主要なクラウドプロバイダーへシームレスにデプロイできる「Build Once, Deploy Everywhere」のアプローチを採用している。UbisoftのThomas Lacroix氏も、このクラウドアグノスティックな設計により、ゲームサーバーバイナリを変更せずにあらゆるクラウドで一貫して専用サーバーを稼働できる点を評価している。

また、単一のサーバープロセスで複数のゲームセッションを安全にホストする機能や、再利用可能なゲームサーバーパターンによる効率化、共通APIによるサーバー管理の簡素化といった機能を備えており、大規模なマルチプレイヤーゲームの運用コスト削減に貢献する。

## 今後の展望

CNCFへの移管は、マルチプレイヤーゲームインフラのオープンスタンダード化を推進する重要な一歩となる。これまでゲーム業界ではプロプライエタリなインフラが主流だったが、Agonesがベンダー中立な基盤として広く採用されることで、業界全体のインフラ標準化が加速する可能性がある。2026年のKubeCon + CloudNativeCon Europe（アムステルダム）では、Mark Mandel氏とUbisoftのJean-François Hubert氏による基調講演が予定されており、Ubisoftにおけるオーケストレーション戦略が紹介される見込みだ。
