---
date: "2026-10-04T19:56:55+09:00"
title: "Dell Container Storage Modulesに6件の重大脆弱性、2件はCVSS10.0の最大深刻度で未認証の完全乗っ取りが可能"
description: "DellがエンタープライズストレージとKubernetesを接続するContainer Storage Modules (CSM)に存在する6件の重大脆弱性を修正し、うち2件はCVSS10.0の最大深刻度で未認証の攻撃者による管理者権限奪取を許す。"
tags:
  - Security
  - Cloud
references:
  - "https://www.bleepingcomputer.com/news/security/new-max-severity-dell-csm-flaws-give-hackers-admin-privileges/"
  - "https://thehackernews.com/2026/10/dell-csm-flaws-enable-unauthenticated.html"
  - "https://cybersecuritynews.com/critical-dell-container-storage-flaws/"
---

## 概要

Dellは、PowerStore、PowerScale、PowerFlex、PowerMax、Unity XTといった同社の主要ストレージ製品群とKubernetes環境を接続する「Container Storage Modules(CSM)」に存在する6件の重大な脆弱性を修正した。このうちCVE-2026-63688とCVE-2026-63692の2件はCVSSスコア10.0の最大深刻度と評価されており、未認証の攻撃者がストレージ基盤全体の管理者権限や、Kubernetesクラスタのノード上でのroot権限を奪取できる。CSM 1.17.0より前のすべてのバージョンが影響を受け、回避策は存在しないため、Dellは管理者に早急なアップグレードを呼びかけている。

## 技術的な詳細

CSMはKubernetes向けのContainer Storage Interface(CSI)ドライバの機能を拡張し、コンテナ化されたワークロードからDellのストレージアレイを利用できるようにするモジュール群である。今回修正された6件の根本原因は、認証機能の欠落や認証情報のハードコーディングといった基本的な設計上の不備に起因する。

最大深刻度の2件のうち、CVE-2026-63688は「csm-authorization-storage」のgRPCサーバーに認証機能が存在しないことに起因し、すべてのストレージアレイの管理者認証情報が露出し、csm-authorizationのセキュリティモデルを完全に迂回できる。Dellはこの脆弱性について「csm-authorizationのセキュリティモデルの完全なバイパスを可能にする」と説明している。もう一方のCVE-2026-63692は、認証プロキシおよびテナントサービスにおける未認証バイパスで、すべてのテナントに対する管理者権限を攻撃者に与える。

これに加えて、CVSS9.9のCVE-2026-67269はContainerStorageModuleのリコンサイラにおける不適切な権限昇格で、低権限の攻撃者がクラスタノード上でroot権限を獲得できる。CVSS9.8のCVE-2026-54472はCSM Authorizationモジュールにハードコードされた認証情報により管理者トークンの偽造を許し、同じく9.8のCVE-2026-61421はJWT認証に公開済みの署名鍵がハードコードされていることで、トークン偽造を可能にする。さらにCVSS9.6のCVE-2026-67273はContainerStorageModuleのカスタムリソースリコンサイラにおけるテンプレートエンジンインジェクションで、Kubernetesシークレットへのクラスタ全体の読み取りアクセスとRBACの改変を許す。これらを組み合わせることで、単一のカスタムリソースを送信するだけでKubernetesクラスタ全体が危険に晒される。

## 影響と対応

Dellはこれらの脆弱性が現時点で実際に悪用された事例は確認していないとしているが、過去にはLazarusグループや中国系とされるAPTグループがDell製品の脆弱性を実際の攻撃に利用した例があり、今回の脆弱性も標的型攻撃の対象となるリスクが指摘されている。対策としてDellはCSM 1.18.0以降への即時アップグレードを推奨しており、回避策が存在しないことに加え、JWT署名鍵のローテーションも併せて実施するよう呼びかけている。Kubernetes上でDellストレージを運用する組織は、影響範囲がストレージ基盤だけでなくクラスタ全体に及ぶ点を踏まえ、優先度の高い対応として扱う必要がある。
