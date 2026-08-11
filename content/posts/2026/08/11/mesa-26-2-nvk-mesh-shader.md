---
date: "2026-08-11T14:22:12+09:00"
title: "Mesa 26.2.0リリース、NVKがメッシュシェーダ対応・KosmicKrispはVulkan 1.4対応を達成"
description: "オープンソースグラフィックスライブラリMesa 26.2.0が公開され、NVIDIA向けNVKドライバのメッシュシェーダ対応やApple Metal向けKosmicKrispのVulkan 1.4対応など多数のVulkan関連改善が盛り込まれた。"
tags:
  - OSS
references:
  - "https://www.phoronix.com/news/Mesa-26.2-Released"
  - "https://9to5linux.com/mesa-26-2-open-source-graphics-stack-officially-released-heres-whats-new"
  - "https://www.gamingonlinux.com/2026/08/mesa-26-2-0-released-with-lots-of-improvements-for-linux-steamos-graphics-drivers/"
---

## 概要

Linux向けオープンソースのOpenGL/Vulkanグラフィックススタックである Mesa の四半期リリース、バージョン26.2.0が2026年8月5日に公開された。今回の目玉はNVIDIA向けVulkanドライバ「NVK」における `VK_EXT_mesh_shader` 拡張への対応で、メッシュシェーダ機能がオープンソースNVIDIAドライバでも利用可能になった。あわせて、Apple Metal上で動作するVulkan実装「KosmicKrisp」がVulkan 1.4対応を達成するなど、対応プラットフォーム全体にわたって着実な機能拡充が行われている。

## 技術的な詳細

IntelのVulkanドライバ「ANV」とAMDの「RADV」には多数の最適化が加えられたほか、Vulkanビデオ処理まわりの継続的な開発や複数の新しいVulkan拡張のマージが行われた。具体的には、RADVで `VK_KHR_maintenance11` が実装され、Arm系GPU向けドライバ「PanVK」では `VK_EXT_conservative_rasterization`(保守的ラスタライゼーション)がサポートされた。またRADVでは、GFX10以降の世代を対象に保護メモリ(protected memory)対応も進められている。

Vulkan以外の領域では、OpenCL実装であるRusticlがOpenCL 3.1に対応した。コンパイラ関連では、Arm Mali GPU向けの新しいコンパイラ「KRAID」がマージされた点も注目される。さらに、AMDの次世代アーキテクチャであるGFX12.1向けグラフィックス機能への初期対応も開始されており、今後のリリースでの拡充が見込まれる。

## 今後の展望

Mesaは四半期ごとの安定版リリースサイクルを継続しており、今回のNVKメッシュシェーダ対応やKosmicKrispのVulkan 1.4対応は、それぞれNVIDIA GPUおよびApple Silicon環境における最新ゲームやグラフィックスアプリケーションの互換性・パフォーマンス向上に直結する。今回の改善はLinuxおよびSteamOSのグラフィックス環境全体の底上げに寄与するものであり、SteamOSを採用するValveの携帯型ゲーミングデバイスなどでの活用も期待される。

なお、9to5linuxおよびGamingOnLinuxの関連記事は本執筆時点でアクセスできなかったため、本稿はPhoronixの報道内容を中心に構成している。
