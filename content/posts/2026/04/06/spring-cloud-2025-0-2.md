---
date: "2026-04-06T02:14:50+09:00"
title: "Spring Cloud 2025.0.2（Northfields）リリース — CVE修正と依存ライブラリのアップデートを含むメンテナンス版"
description: "SpringチームがSpring Boot 3.5.13ベースのメンテナンスリリース「Spring Cloud 2025.0.2（Northfields）」を公開し、セキュリティ修正を含む各モジュールのアップデートを提供した。"
tags:
  - Programming Languages
references:
  - "https://spring.io/blog/2026/04/02/spring-cloud-2025-0-2-aka-northfields-has-been-released/"
---

## 概要

SpringチームはSpring Cloud 2025.0.2（コードネーム「Northfields」）の一般提供開始を発表した。本リリースはSpring Boot 3.5.13をベースとしたメンテナンスリリースであり、Maven Centralにて公開されている。バグ修正と依存関係のアップデートを中心とした内容で、既存ユーザーへのアップグレードが推奨される。

## 主な変更点

今回のリリースでは複数のモジュールにわたってアップデートが行われた。

- **Spring Cloud OpenFeign**: OpenFeign 13.6.1へのアップグレード
- **Spring Cloud Kubernetes**: Fabric8 7.3.2へのアップグレード
- **Spring Cloud Netflix**: Eureka 2.0.6へのアップグレード、および `eureka-client` から `commons-configuration` の除外
- **Spring Cloud Config**: **CVE-2026-22739** のセキュリティ脆弱性修正

特筆すべき点として、Spring Cloud ConfigにおいてCVEの修正が含まれており、セキュリティ上の観点からも早期のアップグレードが望ましい。

## 導入方法

BOMを利用した依存管理による導入が推奨されている。Mavenの場合は `spring-cloud-dependencies` のバージョンを `2025.0.2` に指定することで各モジュールのバージョンを一元管理できる。Gradleでも同様に `dependency-management` プラグインを通じてBOMをインポートする形式に対応している。
