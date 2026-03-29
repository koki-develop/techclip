---
date: "2026-03-30"
title: "Ingress2Gateway 1.0正式リリース、30以上のアノテーション対応でIngress-NGINXからGateway APIへの移行を本格支援"
description: "KubernetesのSIG Networkが移行支援ツールIngress2Gateway 1.0を正式リリースし、Ingress-NGINXの廃止に伴うGateway APIへの移行を包括的にサポートする。"
tags:
  - Cloud
  - OSS
references:
  - "https://kubernetes.io/blog/2026/03/20/ingress2gateway-1-0-release/"
---

## Ingress2Gateway 1.0の概要

KubernetesのSIG Networkは2026年3月20日、Ingressリソースから Gateway APIへの移行を支援するツール「Ingress2Gateway」のバージョン1.0を正式にリリースした。開発はGoogleのBeka Modebadze氏とMicrosoftのSteven Jin氏が中心となって進めている。Ingress-NGINXが2025年11月に廃止を発表し、2026年3月に正式に引退となったことを受け、多くのKubernetesユーザーにとってGateway APIへの移行が急務となっている中でのリリースとなる。

Ingress2Gatewayは、既存のIngressリソースやマニフェストをGateway API形式に変換する移行アシスタントツールである。ファイル、特定のNamespace、またはクラスタ全体からIngressリソースを読み取り、対応するGateway APIマニフェストを生成する。ただし、完全な自動移行ツールではなく、変換不可能な設定の特定や警告の提示も行い、生成結果の手動レビューが必須とされている点が重要だ。

## 1.0での主な改善点

バージョン1.0では、対応するIngress-NGINXアノテーションが従来の3つから30以上へと大幅に拡充された。CORS（Cross-Origin Resource Sharing）、バックエンドTLS、正規表現マッチング、パスリライト、プロキシボディサイズ、タイムアウト設定など、実運用で多用されるアノテーションを幅広くカバーしている。出力先としてはIngress-NGINXのほか、AgentGateway、Envoy Gateway、kgatewayといった実装にも対応しており、`--emitter`フラグで切り替えが可能だ。

もう一つの大きな改善点は、コントローラレベルの統合テストの導入である。実際のクラスタ上で実コントローラを動作させ、ルーティング、リダイレクト、リライトなどのランタイム動作を比較検証する。これにより、変換結果が元のIngress設定と振る舞いの等価性を保っているかを確認でき、エッジケースや予期しないデフォルト値の差異を本番環境に持ち込む前に検出できる。エラーハンドリングと通知のフォーマットも改善され、未対応機能の明確な提示や修正提案が行われるようになった。

## 移行の進め方と今後の展望

推奨される移行手順は3ステップで構成される。まずIngress2Gatewayをインストールし（Go、Homebrew、GitHubリリースからの直接ダウンロードに対応）、次にツールを実行してGateway APIマニフェストを生成し、最後に出力された警告や変換不可能な設定をレビューして手動で対処する。移行は「ワンクリックで完了するものではない」と公式が明言しており、並行環境でのGateway APIコントローラのテストや、動作の等価性検証を行ってからの本番切り替えが推奨されている。

IngressとGateway APIの根本的な設計の違いも理解しておく必要がある。IngressはシンプルだがアノテーションやConfigMap、CRDによる拡張に依存していたのに対し、Gateway APIはモジュラーで拡張性のある設計となっており、KubernetesネイティブのRBACサポートも強化されている。2026年4月22日にリリース予定のKubernetes 1.36ではGateway APIの本格採用がさらに進む見込みであり、まだ移行に着手していないチームにとっては、Ingress2Gateway 1.0を活用した早期の移行計画策定が推奨される。
