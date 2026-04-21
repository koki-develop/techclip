---
date: "2026-04-22T02:29:12+09:00"
title: "GrafanaCON 2026：AIの「盲点」を狙うOSSベンチマーク「o11y-bench」と可観測性ツール群を発表"
description: "Grafana LabsはGrafanaCON 2026でAIエージェントの実運用評価向けOSSベンチマーク「o11y-bench」を公開し、Grafana AssistantをエンタープライズおよびOSS環境にも拡張した。"
tags:
  - OSS
  - AI
references:
  - "https://grafana.com/press/2026/04/21/grafana-labs-targets-the-ai-blind-spot-with-new-observability-tools-announced-at-grafanacon-2026/"
  - "https://www.opensourceforu.com/2026/04/grafana-labs-extends-ai-observability-to-oss-with-open-benchmark-launch/"
---

## 概要

Grafana Labsは2026年4月21日、バルセロナで開催された年次カンファレンス「GrafanaCON 2026」にて、AIシステムの可観測性（オブザーバビリティ）に特化した複数の新機能・新ツールを発表した。同社が「AIの盲点（AI Blind Spot）」と呼ぶ課題、すなわち従来の監視ツールがLLMやAIエージェントの障害パターンに対応しきれていない問題に正面から取り組む内容となっている。Senior Director of AIに新たに就任したMat Ryerは「AIは従来の可観測性が想定していない方法で壊れる」と述べており、専用のアプローチが必要だという認識が今回の発表群の背景にある。

## OSSベンチマーク「o11y-bench」の公開

今回の発表の中核の一つが、AIエージェントを実際のオブザーバビリティタスクで評価するためのオープンソースベンチマーク「o11y-bench」だ。Harborフレームワーク上に構築されており、メトリクス・ログ・トレースにまたがってエージェントのパフォーマンスを測定できる。従来の静的なベンチマークとは異なり、実世界における動的なエージェント動作に焦点を当てている点が特徴で、AI可観測性ツールの品質を客観的に比較・評価できる共通基盤の提供を目指している。

## Grafana Assistantの拡張とGrafana Cloud新機能

Grafana AssistantはこれまでGrafana Cloud専用だったが、今回のアップデートでGrafana Enterprise（オンプレミス）およびGrafana OSSにも対応範囲を広げた。これにより、クラウド環境に限らずセルフホスト環境でもAI支援によるモニタリング・自動化・ワークフローオーケストレーションが利用可能になる。新機能として、専用ワークスペースモード、API アクセス、スケジュール自動化、リモートMCPサーバー統合、スキル習得向けのLearnモード、Teamsとの連携、EUリージョン優先の推論オプションなどが追加された。

Grafana Cloud側では、LLMアプリケーションおよびAIエージェントをリアルタイムで監視する「AI Observability」がパブリックプレビューとして提供開始された。入出力の可視化、実行フローの追跡、継続的な出力評価、データ露出リスク検出などを備え、エージェントの会話をファーストクラスのテレメトリシグナルとして扱えるようになっている。さらに、CursorやGitHub Copilotなどのエージェント駆動開発環境に可観測性クエリを統合するCLIツール「Grafana Cloud CLI（GCX）」も発表された。

## 背景と今後の展望

同社の2026年オブザーバビリティ調査では、回答者の15%がAIの自律的な行動に懐疑的であると回答しており、可視性と安全策に対する需要の高まりが浮き彫りになっている。Senior Director of ProductのJen Villaは「AIシステムは10年前の分散システムのようになりつつある。強力だが、理解するのが難しく、運用するのはさらに難しい」と述べている。Grafana Labsは商用クラウド機能とオープンスタンダードを組み合わせた「オープンコア戦略」を推進しており、o11y-benchのOSS公開はそのコミュニティ拡大への布石とも位置付けられる。AIシステムが分散システムに近い複雑さを持ち始めている現在、オブザーバビリティの専門ベンダーとしての差別化を明確に打ち出した格好だ。
