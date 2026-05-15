---
date: "2026-05-16T02:36:23+09:00"
title: "Linux FoundationがOSSパッケージレジストリ持続可能性ワーキンググループを設立、AI由来の急増トラフィックに対応"
description: "Linux Foundationが「Sustaining Package Registries Working Group」を立ち上げ、Sonatype・Python Software Foundation・Rust Foundationなど主要OSSエコシステムが参加し、AIや自動化ツールによるトラフィック急増に伴うインフラの持続可能性問題に取り組む。"
tags:
  - OSS
references:
  - "https://news.slashdot.org/story/26/05/10/0023237/open-source-registries-join-linux-foundation-working-group-to-address-machine-generated-traffic"
---

## 背景：10兆ダウンロードが示すインフラ危機

オープンソースのパッケージレジストリは今、かつてない規模の需要に直面している。Sonatype のCTO Brian Fox 氏によれば、2025年のパッケージダウンロード数は**10兆件**に達した。この急激な増加の主な要因は、CI/CDパイプライン、AIコーディングアシスタント、セキュリティスキャナーといった自動化ツールが「人間の速度ではなくマシンの速度」でパッケージを取得し続けていることにある。

こうした状況は「持続可能性のギャップ（sustainability gap）」と呼ばれる問題を引き起こしている。多くのレジストリはインフラをボランティアの労働力や企業からのインフラ寄付に依存して運営されており、爆発的なトラフィック増加に対して財政的・組織的な対応が追いついていない状態だ。

## ワーキンググループの概要と参加組織

この状況を打開するため、Linux Foundationは「**Sustaining Package Registries Working Group**」を正式に発足させた。参加組織には、Javaエコシステムを支えるSonatype（Maven Central）、Python Software Foundation、Ruby Central（RubyGems）、Rust Foundation（Crates.io）、OpenJS Foundation、Eclipse Foundation（OpenVSX）、OpenSSF、Packagist、Alpha-Omegaなど、主要言語・エコシステムにわたる幅広い団体が名を連ねている。

ワーキンググループの主な目標は3つある。第一に、インフラ寄付やボランティア労働への依存から脱却するための**持続可能な資金調達モデルとガバナンス構造**の確立。第二に、エコシステム横断での**セキュリティプラクティスの統一と情報共有**の推進。第三に、開発者・企業・政策立案者に対してレジストリ運営の実際のインフラコストを**周知・啓発**することだ。

## 今後の展望

このワーキンググループは、コミュニティを分断させることなくレジストリが持続的に運営できる実践的な解決策の確立を目指している。AIツールの普及とソフトウェアサプライチェーンのセキュリティ強化に対する関心の高まりが重なり、パッケージレジストリへの負荷は今後もさらに増加することが予想される。Linux Foundationという中立的な基盤の下でエコシステムをまたいだ協調体制が構築できるかどうかが、OSSインフラの長期的な安定に向けた鍵となる。
