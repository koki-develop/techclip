---
date: "2026-03-29"
title: "ゲームサーバー管理OSS「Agones」がCNCF Sandboxプロジェクトに、Google主導からコミュニティ主導へ"
description: "GoogleがKubernetes上のゲームサーバーオーケストレーションOSS「Agones」をCNCFにSandboxレベルで寄贈し、ベンダー中立なコミュニティ主導のガバナンス体制へ移行した。"
tags:
  - Cloud
  - OSS
references:
  - "https://www.cncf.io/blog/2026/03/23/agones-moves-to-the-cncf-a-new-era-for-open-source-multiplayer-game-infrastructure/"
---

## 概要

GoogleがKubernetes上でマルチプレイヤーゲームの専用サーバーを管理するオープンソースプラットフォーム「Agones」を、Cloud Native Computing Foundation（CNCF）にSandboxレベルのプロジェクトとして正式に寄贈した。これにより、AgonesのガバナンスはGoogle主導からベンダー中立なコミュニティ主導の体制へと移行する。プロジェクト創設者のMark Mandel氏は「マルチプレイヤーゲームサーバーのホスティングはかつて完全にプロプライエタリなシステムで運用されていたが、オープンソースがゲームを変えた」と述べている。

## Agonesの技術的特徴

Agonesは、Kubernetesを拡張して専用ゲームサーバーのライフサイクル管理を行うプラットフォームである。PC、コンソール、モバイルといったプラットフォームを問わず「一度構築すればどこにでもデプロイできる」設計思想を持ち、オンプレミスのデータセンターから主要なクラウドプロバイダーまで、ゲームサーバーのバイナリを変更することなくクラウド非依存で動作する。単一プロセスで複数のゲームセッションを安全にホストする再利用可能なサーバーパターンをサポートしており、運用の予測可能性を高めている。

## 背景と経緯

Agonesは2017年にGoogleとUbisoftの緊密な共同開発から誕生した。以来、250名以上のコントリビューターを擁し、大手ゲームスタジオで実運用されるなど業界標準のプロジェクトへと成長してきた。UbisoftのThomas Lacroix氏は、Agonesのクラウド非依存な設計により「どのクラウドプロバイダーでも一貫して専用ゲームサーバーを運用でき、効率を改善しながら安定的にキャパシティをスケールできる」と評価している。

## 今後の展望

CNCFへの移管により、Google以外のクラウド事業者やゲームスタジオの参加拡大が見込まれ、マルチプレイヤーゲームインフラのオープンスタンダード化がさらに促進されると期待される。創設者のMark Mandel氏とUbisoftのJean-François Hubert氏は、KubeCon + CloudNativeCon Europe 2026で基調講演を行い、Agonesを活用したUbisoftのオーケストレーション戦略について詳細を発表する予定だ。
