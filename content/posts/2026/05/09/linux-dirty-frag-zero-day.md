---
date: "2026-05-09T02:36:52+09:00"
title: "Linuxカーネルの新ゼロデイ「Dirty Frag」、競合状態不要で主要ディストリビューションのroot奪取が可能に"
description: "Linuxカーネルに長年潜んでいた2つのページキャッシュ書き込み脆弱性を連鎖させた「Dirty Frag」が公開され、Ubuntu・RHEL・Fedoraなど主要ディストリビューションでroot権限昇格が確認された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/new-linux-dirty-frag-zero-day-with-poc-exploit-gives-root-privileges/"
  - "https://thehackernews.com/2026/05/linux-kernel-dirty-frag-lpe-exploit.html"
---

## 概要

セキュリティ研究者のHyunwoo Kim氏は2026年5月7日、Linuxカーネルに存在する新たなローカル権限昇格（LPE）脆弱性「Dirty Frag」を公開した。この脆弱性はカーネルの暗号アルゴリズムインターフェース（algif_aead）に約9年前から潜んでいたとされており、Ubuntu 24.04.4、RHEL 10.1、CentOS Stream 10、AlmaLinux 10、openSUSE Tumbleweed、Fedora 44など主要なLinuxディストリビューションすべてに影響する。権限を持たないローカルユーザーがroot権限を取得できるPoC（概念実証コード）もすでに公開されており、早急な対応が求められる状況だ。なお、今回の早期開示はKim氏ではなく第三者が独自にエクスプロイトを公開したことでエンバーゴが破られたことによるものとされている。

## 技術的な詳細

Dirty Fragは、2つの独立したカーネル脆弱性を連鎖させることで成立する。

- **xfrm-ESP Page-Cache Write**（CVE-2026-43284）：2017年1月のコミットに由来するIPSecサブシステムの欠陥
- **RxRPC Page-Cache Write**（CVE-2026-43500）：2023年6月に導入されたRxRPCサブシステムの欠陥

2つの脆弱性を組み合わせることで、カーネルが所有していないメモリ領域へのページキャッシュ書き込みプリミティブが実現する。Dirty PipeやCopy Failと同じバグクラスに属するものの、タイミングウィンドウに依存しない**決定論的なロジックバグ**であることが最大の特徴だ。競合状態（race condition）を必要とせず、失敗時にカーネルパニックを引き起こさないため、攻撃の信頼性が非常に高い。また、Copy Failに対して有効とされてきたalgif_aeadのブロックリスト緩和策を適用済みの環境でも、この連鎖攻撃は依然として機能することが確認されている。

## パッチと緩和策

CVE-2026-43284（xfrm-ESP）はコミット `f4c50a4034e6` で修正されたが、CVE-2026-43500（RxRPC）については公開時点でパッチが提供されていない。各ディストリビューションの公式パッチを待つ間の暫定的な緩和策として、脆弱なカーネルモジュールを無効化する方法が案内されている。

```bash
sudo sh -c "printf 'install esp4 /bin/false\ninstall esp6 /bin/false\ninstall rxrpc /bin/false\n' > /etc/modprobe.d/dirtyfrag.conf"
```

ただし、このモジュール無効化はIPsec VPNおよびAFS分散ファイルシステムを利用不能にする副作用がある。IPsecを業務で使用している環境では影響を十分に評価したうえで対応する必要がある。ユーザーは各ディストリビューターのセキュリティアドバイザリを監視し、正式なカーネルアップデートが公開され次第、速やかに適用することが推奨される。
