---
date: "2026-04-04T02:16:45+09:00"
title: "Swift 6.3リリースとSwift Buildのデフォルト化、6.3.1のLinux・Windows向け開発も開始"
description: "Swift.orgが2026年3月のエコシステム総括を公開し、Swift 6.3の正式リリースやSwift BuildのSPMデフォルト化、複数のEvolutionプロポーザル承認を報告。同時にLinux・Windows向けSwift 6.3.1のパッチリリース開発が開始された。"
tags:
  - Programming Languages
references:
  - "https://www.swift.org/blog/whats-new-in-swift-march-2026/"
  - "https://forums.swift.org/t/development-open-for-swift-6-3-1-for-linux-and-windows/85715"
---

## Swift 6.3リリースとSwift Buildのデフォルト化

Swift.orgは2026年3月31日、「What's new in Swift: March 2026 Edition」を公開し、3月のエコシステムの主要な動向をまとめた。最大のトピックはSwift 6.3の正式リリースと、SwiftのメインブランチでSwift BuildがSwift Package Manager（SPM）のデフォルトビルドシステムとして採用されたことだ。

Swift BuildのSPM統合は、Appleの Core BuildチームのOwen Voorheesが解説した取り組みで、将来的な標準化に向けた重要なマイルストーンとなる。互換性検証として、swiftpackageindex.com上の数千のオープンソースパッケージを対象にテストが実施されており、エコシステム全体への影響が最小限となるよう慎重に進められている。

## 承認されたSwift Evolutionプロポーザル

3月は複数のSwift Evolutionプロポーザルが承認された。**SE-0509**ではCycloneDXおよびSPDX形式をサポートするSBOM（ソフトウェア部品表）生成機能が追加される。**ST-0021**はXCTestとSwift Testingの相互運用性を改善し、既存のテストスイートと新しいテストフレームワークの共存を容易にする。**SE-0515**では`reduce`操作においてコピー不可型（noncopyable types）がサポートされる。現在レビュー中の**SE-0522**では、`@warn`属性による細粒度のコンパイラ警告制御が提案されている。

## Linux・Windows向けSwift 6.3.1の開発開始

Swift 6.3.1のLinuxおよびWindows向けパッチリリースの開発が正式に開始された。リリースマネージャーはMishal Shah氏が担当し、`release/6.3.1`ブランチへのマージウィンドウは2026年4月10日まで、リリース本体は4月末を予定している。Swift 6.3.1は非Darwin（非Apple）プラットフォームを対象とした月次リリースプロセスに基づくものだ。

コミュニティからはWindows上でのSourceKit-LSPの高CPU使用率（スピニング問題）が6.3.1に含まれるかどうか注目されたが、Alex Hoppen氏はこの修正を6.3.1には取り込まないと説明した。「修正にはstdin解析ロジック全体の書き直しが伴うため、パッチリリースに含めるリスクが高すぎる」とし、Swift 6.4での修正を予定している。この対応はメンテナーがパッチリリースでは安定性を最優先とし、大規模なリファクタリングはメジャーリリースに先送りする方針を堅持していることを示している。
