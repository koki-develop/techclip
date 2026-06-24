---
date: "2026-06-25T02:42:08+09:00"
title: "NGINX Open Sourceにリモートコード実行を許す重大脆弱性2件、F5がパッチ公開"
description: "F5がNGINX Open SourceのHTTP/3 QUICモジュールとHTTP/2プロキシに存在するCVSS 9.2のRCE脆弱性2件を修正するパッチを公開した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/f5-patches-two-critical-nginx-open.html"
---

## 概要

F5は2026年6月18日、NGINX Open Sourceに存在する2件の重大な脆弱性にパッチを公開した。いずれもCVSSスコア9.2と評価されており、認証なしのリモート攻撃者がリモートコード実行（RCE）を達成できる可能性がある。対象となるNGINX Open Sourceのバージョンは、CVE-2026-42530が1.31.0〜1.31.1（1.31.2で修正）、CVE-2026-42055が1.31.1および1.30.0〜1.30.2（それぞれ1.31.2、1.30.3で修正）であり、Gateway Fabric、Instance Manager、Ingress Controller、F5 WAF製品も影響を受ける。公開時点では野放しの悪用は確認されていないものの、F5製品の脆弱性は過去に急速に武器化された事例があるため、速やかなアップデートが強く推奨されている。

## 脆弱性の技術的詳細

**CVE-2026-42530**（CVSS 9.2）は、HTTP/3 QUICモジュール（`ngx_http_v3_module`）に存在するuse-after-free脆弱性だ。セッションレベルのポインタが単方向ストリームよりも長く生存するライフタイムの不一致が根本原因であり、HTTP/3が有効な構成でリモートの未認証攻撃者がこの欠陥を突くことができる。ただし悪用にはASLR（アドレス空間配置のランダム化）が無効化またはバイパス可能な状態であることが条件となる。緩和策としてHTTP/3を無効化することで攻撃経路を遮断できる。

**CVE-2026-42055**（CVSS 9.2）は、HTTP/2プロキシおよびgRPCモジュールに存在するヒープベースのバッファオーバーフローだ。HPACKのvarintエンコーダが予約された4バイトではなく5バイトを出力してしまい、割り当て済みメモリ領域の外に書き込みが発生する。悪用の前提条件として、`proxy_http_version 2`またはgRPCパスの有効化に加え、`ignore_invalid_headers off`の設定と`large_client_header_buffers`が2MBを超えることが必要となる。回避策としては`ignore_invalid_headers off`ディレクティブを削除するか、`large_client_header_buffers`を2MB未満に縮小することが有効だ。

## 推奨される対応

F5は各CVEのドキュメントで脆弱性を修正した具体的なバージョンを案内している。パッチ適用が即座に困難な場合は、各脆弱性に対応した設定ベースの緩和策を暫定的に適用することが重要だ。F5製品の脆弱性は過去にも迅速に悪用コードが出回った実績があるため、対応の優先度を高く設定するべきだろう。
