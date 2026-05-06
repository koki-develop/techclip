---
date: "2026-05-07T02:38:05+09:00"
title: "RustプロジェクトがGSoC 2026で13件採択——応募96件は前年比50%増、コンパイラ・ツールチェーン領域を中心に"
description: "RustプロジェクトはGoogle Summer of Code 2026で96件の応募から13プロジェクトを採択し、前年比50%増の応募数を記録した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://blog.rust-lang.org/2026/04/30/gsoc-2026-selected-projects/"
---

## 概要

Rustプロジェクトは2026年4月30日、Google Summer of Code（GSoC）2026の採択プロジェクトを発表した。今年は96件の応募が集まり、前年比50%増という記録的な数字を達成。その中から13件のプロジェクトが採択された。応募増加の一方でAI生成による低品質な提案も増加しており、メンター陣は応募者との事前のやり取り・過去の貢献実績・提案の質・プロジェクトへの重要性・メンターのキャパシティといった複数の基準で選考を行った。

## 採択された13プロジェクト

採択プロジェクトはコンパイラ、標準ライブラリ、ツールチェーンにまたがる多岐にわたる領域をカバーしている。

- **A Frontend for Safe GPU Offloading in Rust**（Marcelo Domínguez、メンター: Manuel Drehwald）
- **Adding WebAssembly Linking Support to Wild**（Kei Akiyama、メンター: David Lattimore）
- **Bringing autodiff and offload into Rust CI**（Shota Sugano、メンター: Manuel Drehwald）
- **Debugger for Miri**（Mohamed Ali Mohamed、メンター: Oli Scherer）
- **Implementing impl and mut restrictions**（Ryosuke Yamano、メンター: Jacob Pratt・Urgau）
- **Improving Ergonomics and Safety of serialport-rs**（Tanmay、メンター: Christian Meusel）
- **libc: transition differing bit-width time and offset variants**（Adam Martinez、メンター: Trevor Gross）
- **Link Linux kernel and its Modules with Wild**（Vishruth Thimmaiah、メンター: David Lattimore）
- **Migrating rust-analyzer assists to SyntaxEditor**（Shourya Sharma、メンター: Chayim Refael Friedman・Lukas Wirth）
- **Port std::arch test suite to rust-lang/rust**（Sumit Kumar、メンター: Jakub Beránek・Folkert de Vries）
- **Reorganizing tests/ui/issues**（zedddie、メンター: Teapot・Kivooeo）
- **Utilize debugger APIs to improve debug info**（Anthony Bolden、メンター: Jakub Beránek・Jieyou Xu）
- **XDG path support for rustup**（Guicheng Liu、メンター: rami3l）

GPU オフロードや WebAssembly リンク、自動微分（autodiff）、デバッガ改善、`rust-analyzer`のリファクタリングなど、Rustエコシステムの実用性と品質向上を目指すテーマが並んでいる。

## コミュニティの成長と課題

13人のコントリビューターのうちKei、Marcelo、Shouryaの3名は前年度GSoCの経験者で、引き続きRustへの貢献を続ける。一方でメンター不足も表面化しており、プロジェクトへの資金を失ったメンターが複数おり、一部のプロジェクトはキャンセルを余儀なくされた。各プロジェクトは2026年秋の完了を目標に活動を開始する予定で、Rustコミュニティは新世代の開発者を積極的に受け入れながらもメンタリング体制の強化という課題にも向き合っている。
