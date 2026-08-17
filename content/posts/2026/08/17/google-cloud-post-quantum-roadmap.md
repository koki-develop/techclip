---
date: "2026-08-17T20:04:55+09:00"
title: "Google Cloud、2029年完了目標の耐量子暗号(PQC)移行ロードマップを公開"
description: "Google CloudがPQC移行の詳細ロードマップを公開し、SNDL対策・完全性保証・暗号的敏捷性の3領域で2029年までの全面移行を目指す方針を示した。"
tags:
  - Cloud
  - Security
references:
  - "https://cloud.google.com/blog/products/identity-security/pqc-in-plaintext-google-clouds-post-quantum-cryptography-roadmap"
---

## 概要

Google Cloudは8月11日、耐量子計算機暗号(Post-Quantum Cryptography, PQC)への移行に関する詳細なロードマップを公開した。ブログ記事はJai Haridas氏(VP/GM, Regulated and Sovereign Cloud)とMichael Bachman氏(VP/GM, Cloud Foundations)が執筆し、2029年までの完全対応を目標に、「Store Now, Decrypt Later(SNDL)対策」「完全性・否認防止」「暗号的敏捷性を備えた基盤・鍵管理」という3つの領域に分けた段階的な移行計画を示している。背景にあるのは「Harvest Now, Decrypt Later(HNDL)」と呼ばれる脅威で、攻撃者が現在のうちに暗号化通信を記録・保存しておき、将来量子コンピュータが実用化された時点でまとめて復号するリスクへの対応が急務となっている。

すでに実装済みの機能も多い。google.comおよび*.googleapis.comのAPIエンドポイントはFIPS 203として標準化されたML-KEMのハイブリッドモードに対応し、Application/Proxy Load BalancerではX25519MLKEM768によるTLS 1.3の量子安全な鍵交換をオプトインで提供している。またCloud KMSでは鍵カプセル化のML-KEM、署名用のML-DSA(FIPS 204)・SLH-DSA(FIPS 205)が一般提供(GA)済みで、Google内部のサービス間通信を暗号化するALTS(Application Layer Transport Security)についても2025年にPQC対応を完了したという。

## 技術的な詳細

Google CloudはPQCアルゴリズムとして、NISTが標準化した鍵カプセル化メカニズムのML-KEM(FIPS 203)、デジタル署名のML-DSA(FIPS 204)とSLH-DSA(FIPS 205)を採用する。現行のX25519と組み合わせるハイブリッドモード(X25519MLKEM768)を採用することで、既存システムとの互換性を保ちながら段階的にPQCを導入できる設計になっている。またPQC署名はサイズが大きく証明書チェーンの検証に影響を与えるため、ChromeやCloudflareと連携してMerkle Tree Certificatesの実験に取り組んでおり、IETFのPLANTSワーキンググループでの標準化にも関与しているという。

ハードウェア面では、チップレベルの検証を行うCaliptra v2.1、オープンソースのRoot of TrustであるOpenTitan(量子安全ブートは2025年に対応完了)、TPM 2.0 v185などを組み合わせ、2028年までにConfidential ComputingやFIPS 140-3 Level 3準拠のQuantum-Safe Cloud HSMを整備する計画としている。

## ロードマップと責任分担

3つの領域それぞれに達成目標年が設定されている。SNDL対策(顧客ワークロード、管理者・開発者フロー、データパイプラインの保護)は2027年完了を目標に、Cloud VPNやCloud Interconnect、GKE Service Mesh、Tinkなどが2026〜2027年にかけて順次対応する。完全性・否認防止(ソフトウェアサプライチェーン保護、証明書発行、Cloud IAM)と、基盤・鍵管理(EKM、Google Workspace Client-Side Encryptionなど)はいずれも2028年完了を目標としている。

移行にあたってはGoogleと顧客の責任分担が明確化されており、Googleはネットワークの量子安全化や転送中暗号化、ハードウェアの完全性保証を担う一方、顧客側はアプリケーションのPQCハンドシェイク対応や鍵のライフサイクル管理、サービス設定の更新を担う「責任共有モデル」となる。この動きは、2030〜2035年に従来型アルゴリズムの段階的廃止を求めるNSAのCNSA 2.0や、移行パスを定めるNIST IR 8547といった規制動向とも歩調を合わせたものだ。

## 顧客への推奨事項

Google Cloudは顧客に対し、(1) Cloud Asset InventoryやWizの暗号資産評価ツールを用いた暗号資源のインベントリ把握、(2) BoringSSLやChrome、各種SDKなどPQC対応ソフトウェアへの更新、(3) 量子安全なAPIやロードバランサーを用いた検証、という3段階での準備を推奨している。今後数年で主要クラウドサービスの量子安全化が段階的に進む見通しであり、企業側も自社システムの暗号資産棚卸しを早期に始めることが求められそうだ。
