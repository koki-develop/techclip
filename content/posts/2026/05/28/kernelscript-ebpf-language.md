---
date: "2026-05-28T03:03:28+09:00"
title: "KernelScript 0.1：eBPF・ユーザー空間・カーネル空間を単一コードで扱う型安全DSLが登場"
description: "Linux Open-Source SummitでデビューしたKernelScript 0.1は、eBPF開発の複雑さを解消するApache 2.0ライセンスの型安全ドメイン固有言語で、XDPやTC、プローブなど主要なeBPFプログラム種別をサポートする。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://www.phoronix.com/news/KernelScript"
  - "https://linuxiac.com/kernelscript-0-1-debuts-as-a-new-language-for-ebpf-development/"
---

## 概要

Linux Open-Source SummitにてKernelScript 0.1が発表された。KernelScriptはeBPF・ユーザー空間・カーネル空間の開発を単一のコードベースに統合することを目的とした型安全なドメイン固有言語（DSL）で、Apache 2.0ライセンスのオープンソースとして公開されている。従来、eBPFプログラムをC言語で手書きするには複雑な知識とボイラープレートが必要だったが、KernelScriptはその複雑さを抽象化し、必要なコードやMakefile、カーネルモジュール統合コードを自動生成することで開発効率の向上を目指している。

## 技術的な詳細

KernelScriptは主要なeBPFプログラム種別を幅広くサポートしている。ネットワークパケット処理向けのXDP（eXpress Data Path）、トラフィック制御向けのTC（Traffic Control）、カーネル関数のトレーシングに使うプローブ、そしてパフォーマンスイベントプログラムが対象となっている。データ構造についてはハッシュマップ、CPU別配列、LRU（Least Recently Used）マップ、ピンマップといったeBPF標準の各種マップ型に対応する。

さらに高度な機能として、テールコールの自動化、dynptrによる動的ポインタ処理、プログラムライフサイクルチェック、kfunc（カーネル関数）統合もサポートされている。これらの機能を一つの言語で統一的に扱えることで、ネットワーク・トレーシング・可観測性・セキュリティ・パフォーマンス分析といったeBPFの幅広いユースケースにおける開発体験が改善されることが期待される。

## 現状と今後の展望

開発チームは現時点のリリースをあくまで実験的なものと位置づけており、構文やAPIは今後変更される可能性があるとして本番環境での使用を推奨していない。バージョン0.1という初期段階のリリースながら、eBPF開発の敷居を下げるという方向性は明確であり、今後のコミュニティの反応や継続的な開発進捗に注目が集まる。

