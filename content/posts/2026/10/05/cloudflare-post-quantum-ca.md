---
date: "2026-10-05T18:24:17+09:00"
title: "Cloudflareが独自認証局を設立へ、GlobalSignのルート鍵材料でポスト量子証明書を2027年に本番発行"
description: "Cloudflareが公開認証局(CA)の設立を発表し、GlobalSignからルートCA鍵材料を取得して量子計算機時代に備えたMerkle Tree Certificatesの本番発行を2027年第1四半期に開始する計画を示した。"
tags:
  - Security
  - Cloud
references:
  - "https://www.cloudflare.com/press/press-releases/2026/cloudflare-announces-public-certificate-authority-for-the-post-quantum-web/"
  - "https://www.darkreading.com/cloud-security/cloudflare-announces-public-certificate-authority-post-quantum-web"
  - "https://siliconangle.com/2026/09/29/cloudflare-to-become-a-public-certificate-authority-with-post-quantum-certificates/"
---

## 概要

Cloudflareは9月29日、自社で公開認証局(CA)となる計画を発表した。GlobalSignからルートCAの鍵材料を取得する取引を進めており、クローズは今後2ヶ月以内を目標としている。確立済みのルート証明書を引き継ぐことで、古いブラウザや端末からも互換性のある証明書を即座に発行できる体制を整える狙いだ。Matthew Prince CEOは、2014年に提供を開始し「一夜にしてウェブ上の暗号化トラフィックを倍増させた」とされるUniversal SSLの延長線上にある取り組みと位置づけ、「量子計算機の時代が来る前にウェブセキュリティを強化することは、インターネットの歴史上最大級の調整課題の一つだ」と述べている。

## ポスト量子証明書とMerkle Tree Certificates

今回の構想の核心は、量子計算機による解読に耐える「ポスト量子証明書」の発行基盤を整えることにある。ポスト量子署名アルゴリズムは出力サイズが2,420バイトに達し、現在標準的な楕円曲線署名の64バイトと比べて大幅に大きい。この負荷を回避するため、Cloudflareは軽量な証明書形式「Merkle Tree Certificates(MTC)」を採用する。MTCは、信頼された公開ログに証明書が登録されていることを軽量な証明(proof)で示す仕組みで、各接続ごとに大きなポスト量子署名を送信する必要をなくす。CloudflareはこのMTCについてIETF(Internet Engineering Task Force)のドラフト仕様を共同執筆しており、すでにGoogleのChromeチームとの実験的運用に成功している。Let's Encryptも2027年までの本番発行を目指しているとされ、業界全体で同時並行的に移行が進んでいる状況がうかがえる。Cloudflareはブラウザ各社――Chrome、Apple、Microsoft、Mozilla――のルートプログラムへの参加を申請済みで、承認を受けた後に従来型証明書の発行を開始し、MTCについては2027年第1四半期の本番発行を計画している。

## 背景と今後の影響

現行の証明書インフラは、量子計算機による脅威を想定せずに設計されてきた。さらに、Cloudflareが利用する証明書は現在、少数の外部発行者(3社)に依存しており、信頼が特定の発行者に集中することでシステミックリスクが生じている点も課題とされてきた。自ら認証局となることで、Cloudflareはこうした外部依存からの脱却と、量子計算機が既存の暗号方式を破る可能性がある「数年以内」という脅威への備えを同時に進める構えだ。発表では、リアルタイムの公開ダッシュボードによる運用の透明性(「ガラスボックス」運用)、RFC 9773を活用したゼロダウンタイムでの障害対応、そして単一システム内で従来型証明書とポスト量子証明書を統一的に管理できる仕組みも提供予定の特徴として挙げられている。ウェブ全体のPKI(公開鍵基盤)が量子耐性へと移行する転換点において、インターネットの主要インフラ事業者の一つであるCloudflareが自ら認証局を運営するという決定は、他の大手プラットフォームの対応にも影響を与える可能性がある。
