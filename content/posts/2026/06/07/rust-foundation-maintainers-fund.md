---
date: "2026-06-07T02:31:15+09:00"
title: "Rust Foundation、コアメンテナーへの継続支援を目指す「Maintainers Fund」を正式発足"
description: "Rust Foundationが「Rust Foundation Maintainers Fund」を正式ローンチし、Rustプロジェクトのコアメンテナーに安定した長期資金を提供する仕組みを整備した。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://blog.rust-lang.org/2026/06/02/launching-the-rust-foundation-maintainers-fund/"
---

## 概要

Rust Foundation Leadership Councilは2026年6月2日、Rustプロジェクトのメンテナーを経済的に支援するための「Rust Foundation Maintainers Fund（RFMF）」を正式に立ち上げたと発表した。本基金はRFC #3931として承認された提案を具体化したもので、「Funding team」と「Maintainer in Residence」という2つのプログラムを軸に、コアメンテナーへの継続的かつ安定した報酬を実現することを目指す。設立の背景には、重要なRustメンテナーが企業の予算削減によって資金を失う傾向が観察されているという問題意識がある。

## 2つのプログラムの詳細

**Funding team**は、メンテナーの資金状況を把握し、チームリーダーとの定期的な会合を通じて保守ニーズを洗い出したうえで、企業スポンサーへの投資機会を提案するチームだ。個人や企業からの寄付・支援をメンテナーへの報酬として適切に配分する調整役を担う。

**Maintainer in Residence（MiR）**プログラムは、既存のRustプロジェクトメンテナーに対し、コンパイラ・標準ライブラリ・Cargo・Clippyといった重要領域の保守業務へ専念できる雇用機会を提供する。対象業務は大規模なリファクタリング、コードレビュー、新機能実装の障害排除、課題トリアージ、他の貢献者へのメンタリングなど多岐にわたる。勤務形態は原則フルタイムに近いが、保守領域の特性に応じて柔軟に対応するとされている。

## 背景と資金調達の方法

RFMFはPython Software Foundation（PSF）が実施している「Developer in Residence」モデルに着想を得ており、設計にあたってPSFとの協議も行われた。Rustの産業利用が急速に広がる一方、持続的な保守を担う人材への安定した資金提供が課題となっていたため、業界の変動に左右されにくい独立した資金源の確立が目標とされている。

資金調達は個人向けにはGitHub Sponsorsを通じた「rustfoundation」組織への寄付、企業向けにはGitHub Sponsorsまたは直接の問い合わせ（contact@rustfoundation.org）という2つの経路が用意されている。集まった収益はすべてRustプロジェクトのメンテナー支援に直接充てられると明記されている。

## 今後の展望

Rust Foundationは今後数か月以内に最初のMaintainer in Residenceを雇用し、ブログで発表する予定としている。本プログラムは既存の支援施策（プログラム管理プログラム、コンパイラ運用プログラム、RustNL Maintainers Teamによる雇用など）を補完する形で運用される。まだ新しい取り組みであり、進行しながら制度を磨いていく方針が示されており、オープンソースプロジェクトのサステナビリティ確保に向けた新たなモデルとして注目される。
