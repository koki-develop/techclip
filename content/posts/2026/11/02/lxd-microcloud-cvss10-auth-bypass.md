---
date: "2026-11-02T08:07:03+09:00"
title: "LXD/MicroCloudにCVSS 10.0の認証バイパス、秘密鍵なしで信頼済みクライアントになりすまし可能"
description: "CanonicalのLXD・MicroCloud（およびIncus）にmTLS証明書チェーンの検証不備による最大深刻度の認証バイパス脆弱性CVE-2026-112816が見つかり、修正版がリリースされた。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/11/critical-lxd-and-microcloud-flaw-cvss.html"
  - "https://discourse.ubuntu.com/t/security-advisory-critical-vulnerability-found-in-canonical-lxd-and-microcloud/90557"
  - "https://blog.ostorlab.co/lxd-incus-mtls-authentication-bypass-cve-2026-112816.html"
---

## 概要

Canonicalが開発するコンテナ/VM管理ツールLXDと、そのクラスタ構築ツールMicroCloud、および同系統のオープンソース実装Incusに、CVSSスコア10.0(最大深刻度)の認証バイパス脆弱性CVE-2026-112816が発見された。Ubuntuのセキュリティアドバイザリによると、脆弱性は「検証されていないクライアント証明書チェーンによる認証バイパス」であり、攻撃者はターゲットの秘密鍵を持たずとも、公開されている証明書さえ入手できれば信頼済みクライアントになりすませる。攻撃に特別な権限は不要で、デーモンのHTTPS APIにネットワーク経路でアクセスできることが条件となる。Canonicalは2026年10月29日に全チャンネルで修正版をリリースしており、現時点で悪用の報告はないものの、早急なアップデートが呼びかけられている。

## 脆弱性の技術的詳細

問題の核心は、mTLS(相互TLS)認証におけるクライアント証明書チェーンの検証ロジックにある。セキュリティ研究者Ostorlabの分析によれば、修正前のコードは`r.TLS.PeerCertificates`に含まれるクライアント提示の証明書チェーンを1枚ずつループし、それぞれを個別に信頼ストアと照合していた(`for _, i := range r.TLS.PeerCertificates { trusted, fingerprint := localUtil.CheckTrustState(*i...)`)。本来、TLSハンドシェイクで秘密鍵の所有が暗号学的に証明されるのはチェーン先頭の「リーフ証明書」のみであり、途中に追加された証明書はクライアントが任意に添付できる。しかし検証ロジックはこの違いを区別せず、チェーン中のどの証明書が信頼ストアにマッチしてもそれを「信頼済み」と判定してしまっていた。

結果として、攻撃者は(1)ハンドシェイク中などの経路で入手可能な、なりすまし対象の公開証明書を取得し、(2)自身の秘密鍵・証明書でAPIに接続する際、(3)入手した公開証明書を自分の証明書チェーンに追加して提示するだけで、(4)信頼済みクライアントとして認証を通過できた。認証が突破されると、なりすまされたアカウントの権限でクラスタやVM/コンテナへのアクセスが可能になり、対象が特権アカウントであればホストマシンのroot権限相当まで到達し得る。MicroCloudではクラスタ参加時に公開証明書が交換される運用上、新規メンバーの証明書を傍受してなりすます経路も指摘されている。脆弱性はIncusプロジェクトの開発者Stéphane Graberが報告し、修正コミットは10月13日付で作成、CVEは10月30日に公開された。各社の勧告に公開PoCへのリンクはなく、本稿執筆時点で既知の悪用事例も確認されていない。

## 影響範囲と対応

影響を受けるのはLXD 4.0.14、5.0.10、5.21.8以前、および6.9.0〜6.10.0の各系列、MicroCloudの対応する旧バージョン、およびIncus 7.6.0より前の全バージョン。Canonicalは2026年10月29日にLXD 6.10.1(6/stable)、5.21.9(5.21/stable)、5.0.11(5.0/stable)、4.0.15(4.0/stable)、MicroCloud 3.4.1(3/stable)、2.1.5(2/stable)をリリースし、Incusプロジェクトも翌30日にIncus 7.6.0をリリース済みだ。推奨される対応は`sudo snap refresh lxd`および`sudo snap refresh microcloud`によるアップデートのみで、恒久的な回避策は提供されていない。アップデートが即時に行えない場合の緩和策として、`core.https_address`設定でネットワークAPIへのアクセス自体を制限する方法が挙げられている。米CISAも10月30日付でこの脆弱性の深刻度評価を行っており、クラスタ環境でLXD・MicroCloud・Incusを運用する管理者には、影響範囲の確認と優先的なパッチ適用が強く求められる。
