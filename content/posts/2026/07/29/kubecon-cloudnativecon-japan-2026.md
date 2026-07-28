---
date: "2026-07-29T02:33:54+09:00"
title: "KubeCon + CloudNativeCon Japan 2026開幕、GPUスケジューリングとOpenTelemetry卒業がAI時代のクラウドネイティブ基盤を象徴"
description: "横浜で開幕したKubeCon + CloudNativeCon Japan 2026で、KubernetesのGPUスケジューリング強化とOpenTelemetryのCNCF卒業が焦点となり、AIエージェント時代の可観測性基盤としてのクラウドネイティブスタックの進化が示された。"
tags:
  - Cloud
  - AI
references:
  - "https://www.techtimes.com/articles/321774/20260728/kubecon-japan-2026-kubernetes-gpu-scheduling-otel-graduation-converge-ai-era.htm"
  - "https://opentelemetry.io/blog/2026/kubecon-japan/"
  - "https://www.cncf.io/announcements/2026/05/13/cncf-debuts-kubecon-cloudnativecon-japan-2026-schedule/"
---

## 概要

KubeCon + CloudNativeCon Japan 2026が横浜のPACIFICO Yokohamaで開幕した。前回開催がチケット完売となった人気を受けて2回目の開催となる今回は、「グローバルなAI経済に求められる信頼性とスケールを実現するため、クラウドネイティブスタックを標準化する」ことを主軸に据え、KubernetesのGPUスケジューリング機能の進化と、5月にCNCFグラデュエーション(卒業)を果たしたOpenTelemetryを軸とした可観測性強化が主要テーマとして取り上げられた。カンファレンスはAI + ML、Observability、Platform Engineering、Operations + Performance、Security、Cloud Native Noviceの6トラックで構成され、AI/MLトラックではGPU管理やワークロードオーケストレーション、AIエージェント支援に関するセッションが多数組まれている。

## GPUスケジューリングの進化

Kubernetesのリソース管理は、AIワークロードの急増に対応する形で大きく前進している。Dynamic Resource Allocation(DRA)はKubernetes 1.34で正式にGA(一般提供)となり、続くKubernetes 1.36ではWorkload Aware SchedulingとDRAを組み合わせたネイティブGPUスケジューリング機能に加え、安定版となったきめ細かいKubelet認可(fine-grained Kubelet authorization)も導入される。会期中には、IBM ResearchとEricssonによる「Sustainability by Design: Leveraging DRA for Energy-Efficient Kubernetes Clusters」など、DRAを活用してGPUクラスタのエネルギー効率を高める具体的な取り組みを紹介するセッションも予定されており、GPUリソースの効率的な割り当てが持続可能性の観点からも重要な論点になっていることがうかがえる。

## OpenTelemetryのCNCF卒業とエージェント可観測性

もう一つの大きな節目が、OpenTelemetryの5月のCNCFグラデュエーションである。この卒業を記念し、7月30日にはAppleのAlolita Sharma氏とGrafana LabsのTed Young氏による基調講演「OpenTelemetry Celebrates Graduation and the Next Era of Agentic Observability」が行われる。会期初日のコミュニティデー(7月28日)ではLayerXの大平氏(Yuzuru Ohira)が「Building AI Agent Observability with OpenTelemetry」と題したセッションを、主会議2日目にはGrafana LabsのNicole van der Hoeven氏が「The Great Doubt: What Building an AI Agent Taught Us About Trust」と題した講演をそれぞれ行う予定で、いずれもAIエージェントのふるまいや信頼性をどう可観測化するかがテーマとなっている。ベンダー中立な計装標準として成熟したOpenTelemetryが、GPUネイティブなクラウド基盤やAIエージェントの動作追跡といった新領域に適用範囲を広げつつある様子が、これらのセッション構成から見て取れる。

## 今後の展望

DRAのGA、OpenTelemetryのCNCF卒業、そしてAIエージェント向け認可を担うKeycloak-MCPの登場という3つの節目がほぼ同時期に重なったことは、クラウドネイティブ技術がAIワークロードを前提とした基盤へと本格的にシフトしていることを象徴している。GPUリソースの効率的なスケジューリングと、エージェントの挙動を含めた可観測性の両輪が整備されることで、企業がAIワークロードを本番環境で安定的に運用するための土台が今後さらに強化されていくとみられる。
