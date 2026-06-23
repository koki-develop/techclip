---
date: "2026-06-24T02:40:18+09:00"
title: "Squidプロキシに29年来の脆弱性「Squidbleed」（CVE-2026-47729）、HTTPリクエスト平文が漏洩の恐れ"
description: "1997年から存在するSquidプロキシのFTPパーサーの脆弱性「Squidbleed」（CVE-2026-47729）が公開され、共有プロキシ環境で他ユーザーのHTTPリクエストや認証情報が漏洩する恐れがある。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/29-year-old-squid-proxy-bug-squidbleed.html"
  - "https://www.securityweek.com/decades-old-squid-proxy-flaw-squidbleed-can-expose-user-data/"
  - "https://www.scworld.com/brief/squid-proxy-vulnerability-dubbed-squidbleed-discovered"
---

## 概要

広く使われているオープンソースのWebキャッシュプロキシ「Squid」に、1997年から存在していた脆弱性「Squidbleed」（CVE-2026-47729）が2026年6月22日に公開された。CVSSスコアは6.5（中程度）で、ヒープオーバーリードによって同一プロキシを利用する他ユーザーのHTTPリクエストや認証情報が平文で漏洩する可能性がある。名称はOpenSSLの重大脆弱性「Heartbleed」に類似したメモリ露出の性質にちなんで命名された。

## 技術的な仕組み

脆弱性はSquidのFTPディレクトリリストパーサー（`FtpGateway.cc`）に存在する。攻撃者が制御するFTPサーバから不正なファイルリスト行を送り込むと、パーサーのポインタがメモリバッファの境界を越えて読み込みを続ける。Squidは使い終わったバッファをゼロクリアせずに再利用するため、直前に処理した別ユーザーのHTTPリクエストデータがそのままメモリに残り、攻撃者に漏洩してしまう。これによりセッショントークン、認証情報、APIキーなどが窃取される恐れがある。なお、標準的なHTTPS通信（TLSトンネル）は影響を受けず、平文のHTTP通信またはSquidがTLSを終端する構成に限定される。

## 影響範囲と緩和策

最もリスクが高いのは、企業ネットワーク、学校、公共Wi-Fiなど、複数ユーザーが同一プロキシを共有する環境だ。攻撃の成立にはプロキシからアクセス可能なFTPサーバの制御が必要であるものの、FTPとポート21はSquidのデフォルト設定で有効化されているため、悪用のハードルは低い。

緩和策としては、FTP機能が不要な場合に**FTPサポートを完全に無効化**することが最も効果的だ。修正パッチは2026年4月にSquid version 8へマージされ、同年6月リリースのversion 7.6に搭載された。パッチの適用時は`FtpGateway.cc`にNUL終端チェックが含まれていることを確認されたい。

## 発見の経緯

脆弱性はセキュリティ企業Calif.ioの研究者チームが発見した。注目すべきは、AnthropicのClaude Mythosモデルを活用してパーサーのバグを検出した点であり、AIを活用した脆弱性探索の実例として広く注目されている。29年にわたって見過ごされてきた脆弱性を機械学習モデルが検出したことは、AIを用いたセキュリティ研究の有効性を示す事例として業界に与える影響は大きい。
