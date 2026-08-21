---
date: "2026-08-21T14:08:46+09:00"
title: "Docker、自社開発の新ハイパーバイザ「Docker VMM」をパブリックベータ公開　起動速度とファイルI/Oを大幅改善"
description: "DockerがDocker Desktop向けに自社開発した新ハイパーバイザ「Docker VMM」のパブリックベータを公開し、コンテナ起動やファイルI/Oの高速化、メモリ管理の改善を実現した。"
tags:
  - Cloud
  - OSS
references:
  - "https://www.publickey1.jp/blog/26/dockerdocker_vmm.html"
  - "https://www.infoq.com/news/2026/08/docker-vmm-layer/"
---

## 概要

Docker社は、Docker Desktop向けに自社開発した新しいハイパーバイザ「Docker VMM」のパブリックベータを公開した。Docker Desktopはホストマシン上に仮想マシンを起動し、その内部でコンテナを稼働させる仕組みを取っているが、これまでWindows版ではHyper-V、macOS版では前世代のDocker VMMというサードパーティ由来の仮想化コンポーネントに依存していた。今回発表された新しいDocker VMMは、Dockerが「仮想化スタック全体を自社で所有し、コンテナワークロード向けにエンジンの各部分を最適化できる」ことを目的に一から開発したもので、Windows版・macOS版ともにDocker Desktop v4.86から利用可能になっている。

## 技術的な詳細

新しいDocker VMMがもたらす改善点は主に3つある。まず、コンテナの初回起動時やプロジェクト切り替え時、再起動時における起動速度の向上だ。次に、ホストOSとコンテナ間のファイル共有の高速化で、コード編集やコンパイル、テストといった開発ワークフローで体感できるレベルの改善が見込めるという。さらに、メモリ管理の改善として、アイドル状態のコンテナが使用していない未使用メモリをホストOS側に返却する仕組みが導入された。Windows環境においては、Dockerとして初の自社開発ハイパーバイザとなり、WSL(Windows Subsystem for Linux)が持つ性能とHyper-Vによる分離性を両立させる設計になっている点も特徴だ。

## 提供状況と今後の展望

現時点では、macOS版は自動的に新しいDocker VMMへ切り替わり、Windows版は設定から任意に有効化できるオプトイン方式となっている。Docker社は2026年10月末を目標に正式版(GA)をリリースし、Windows・macOS・Linuxの3プラットフォームすべてでデフォルトの仮想化エンジンとする計画を示している。現状Linux版は未対応だが、GA版のタイミングでの対応が予定されている。また、このVMMはDocker Desktopだけでなく、Docker Sandboxesや、AIエージェント向けの隔離実行環境にも今後統合される見通しで、Dockerが仮想化基盤を軸にコンテナ実行環境全体の性能と柔軟性を底上げしようとしている姿勢がうかがえる。
