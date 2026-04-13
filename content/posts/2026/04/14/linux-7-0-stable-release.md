---
date: "2026-04-14T02:30:55+09:00"
title: "Linux 7.0正式リリース、自己修復XFSとRust公式サポートを含む多数の改善"
description: "Linus TorvaldsがLinuxカーネル7.0を正式リリースし、XFSの自己修復機能やRust言語サポートの正式化、Intel/AMDの最新CPU対応など幅広い強化が加えられた。"
tags:
  - OSS
references:
  - "https://www.phoronix.com/news/Linux-7.0-Released"
  - "https://www.theregister.com/2026/04/13/linux_kernel_7_releaseed/"
  - "https://itsfoss.com/news/linux-kernel-7-0-release/"
---

## 概要

Linuxカーネル7.0が2026年4月13日にLinus Torvaldsによって正式リリースされた。バージョン7.0への移行はカーネル開発の慣例に従ったもので、6.19に達したタイミングで混乱を避けるために番号を繰り上げた。Torvaldsはリリースを総評して「小さな修正が多く、全体的に問題なく落ち着いた（benign）サイクルだった」と述べており、今回のリリースは革命的な変更よりも着実な改善の積み重ねとなっている。なお、本バージョンはLong-Term Support（LTS）版ではなく、引き続きLinux 6.18が2028年12月まで対応するLTSリリースとなる。

## ハードウェアサポートの強化

Intel面ではNova Lakeオーディオのサポートが標準NVLバリアントに拡張され、従来のSシリーズのみの対応から幅が広がった。Intel Arc GPU向けのXeドライバーはシャットダウン制限値やメモリコントローラー温度、個別のVRAMチャンネル温度など詳細な温度情報を公開するよう改善された。また、Panther LakeがGSCファームウェアのロードとProtected Xe Path（PXP）に対応し、Diamond RapidsはPCIe経由での高速データ転送を実現するNTBドライバーサポートを獲得した。

AMD面ではZen 6向けにブランチ予測やキャッシュ活動、TLBオペレーションに関するパフォーマンスカウンターサポートがマージされた。KVM仮想化においてはReturn Address Predictor Security（ERAPS）のサポートが強化され、Return Stack Bufferの容量が32エントリーから64エントリーに倍増した。また、今後のRDNAバリアントに向けた新しいグラフィックスIPブロックの有効化や、NPU統合に向けた準備も進められている。その他、ARM、RISC-V、Loongsonプロセッサへのサポートも強化されており、RISC-VはユーザースペースのControl-Flow Integrity（CFI）サポートを獲得した。

## ファイルシステムと開発環境の改善

ストレージ面での注目は、XFSに追加された自律的な自己修復機能だ。新たに導入された`xfs_healer`デーモンが、ファイルシステムがマウントされたままの状態でメタデータの障害を自動検出し修復する仕組みを提供する。Btrfsについてはより大きなブロックサイズへのDirect I/Oサポートや実験的なremap-tree機能が追加され、EXT4は遅延エクステント分割による並行書き込みパフォーマンスが向上した。

開発環境においては、Rust言語によるカーネル開発のサポートが「実験的」のステータスを脱して正式サポートとなった大きな節目を迎えた。ネットワーク面ではWiFi 8のUltra-High Reliability（超高信頼性）に向けた下地が実装されたほか、ASUS製マザーボードのセンサーサポートも拡充されている。

## AIとカーネル開発の新潮流

今回のリリースではLinus Torvalds自身がAIのカーネル開発への影響について言及した点も注目された。TorvaldsはリリースメールにおいてAIツールの普及によるバグ発見の増加を予想し、「AIツールの活用がしばらくはコーナーケースを見つけ続けるだろう。これが『新しい常態』になるかもしれない」とコメントした。この見解は、メンテナーのGreg Kroah-Hartmanが以前指摘したAIによるカーネルバグ検出の有効性とも一致しており、AIがカーネル開発のエコシステムに新たな側面をもたらしつつある状況を示している。
