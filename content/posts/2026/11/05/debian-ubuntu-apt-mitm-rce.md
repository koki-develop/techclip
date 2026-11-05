---
date: "2026-11-05T18:09:42+09:00"
title: "DebianとUbuntuのAPTに中間者攻撃でroot権限コード実行を許す脆弱性、再試行処理が原因"
description: "APTのHTTPダウンロード再試行処理に起因する脆弱性CVE-2026-109518が見つかり、中間者攻撃者が正規パッケージを悪意あるものに差し替えてroot権限でコードを実行できる状態だった。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/11/debian-and-ubuntu-apt-flaw-lets-mitm.html"
  - "https://ubuntu.com/blog/apt-vulnerability-fixes-available"
  - "https://www.phoronix.com/news/Debian-APT-MITM-RCE"
---

## 概要

DebianとUbuntuのパッケージ管理システムAPTに、ネットワーク経路上の攻撃者が正規のパッケージを悪意あるコードに差し替え、root権限で任意のコードを実行できる脆弱性(CVE-2026-109518、CVSS 4.0で7.7)が見つかった。APT開発者によれば、攻撃はパッケージのインストール時に発生し、「攻撃者はHTTPリダイレクトと通常の一時的なサーバーエラーを利用して、APTにダウンロードを再試行させる」ことで成立する。攻撃者は悪意あるミラーサーバーやプロキシ、あるいはネットワーク上の中間者的な位置からHTTP通信を改ざんできる立場にあればよく、特別な権限は不要とされる。

## 脆弱性の仕組みと影響範囲

脆弱性の核心は、APTのHTTPバックエンドがダウンロード失敗時の再試行処理(`Acquire::Retries`が非ゼロの場合)を行う際に、署名検証に失敗してもインストールを強制してしまう点にある。これにより、経路上の攻撃者がHTTP通信を操作して攻撃者制御の.debパッケージを送り込み、通常は防がれるはずの署名検証を回避してroot権限を取得できる。

デフォルトで影響を受けるのはDebian 12以降およびUbuntu 22.04 LTS以降で、Debianのtesting版も11月4日時点で脆弱な3.3.5のままだった。Debian 11とUbuntu 20.04は再試行設定が有効になっている場合に限り影響を受ける。Debian系・Ubuntu系の派生ディストリビューションにも同様の問題が及ぶ可能性がある。なお、攻撃はHTTP経由であることが前提とされている。Canonicalのアドバイザリによれば、HTTPSでパッケージを取得している場合はこの脆弱性の影響を受けない。

## 修正パッケージと対策

CanonicalはUbuntuの幅広いリリース向けに修正版を公開した。サポート対象のLTSだけでなく、Extended Security Maintenance(ESM)の対象であるTrusty 14.04からStonking 26.10まで、合計8リリースに修正パッケージが提供されている。

| リリース | 修正バージョン |
|---------|------------|
| Trusty 14.04 LTS | 1.0.1ubuntu2.24+esm4 |
| Xenial 16.04 LTS | 1.2.36+esm1 |
| Bionic 18.04 LTS | 1.6.19+esm1 |
| Focal 20.04 LTS | 2.0.12+esm1 |
| Jammy 22.04 LTS | 2.4.15ubuntu0.1 |
| Noble 24.04 LTS | 2.8.4ubuntu0.1 |
| Resolute 26.04 LTS | 3.2.1ubuntu0.1 |
| Stonking 26.10 | 3.3.3ubuntu0.1 |

Debian側も11向けに修正版2.2.5をリリースしている。Canonicalは修正パッケージの適用に加えて、パッケージ取得元のURLをHTTPからHTTPSに切り替えることや、`sudo apt update && sudo apt upgrade -o Acquire::Retries=0`のように再試行を無効化して更新を適用することを緩和策として案内している。また、Ubuntu 16.04以降では標準で有効なunattended-upgradesにより、多くの環境では24時間以内に修正が自動適用される見込みだとしている。

## 今後の対応

今回の問題は、セキュリティ機構であるはずの署名検証がエラー処理の抜け道によって無効化されるという典型的なパターンであり、長年使われてきたAPTの再試行ロジックに潜んでいた点が注目される。管理者は自動更新に依存せず、該当する修正バージョンが適用されているかを早期に確認することが望まれる。また、HTTPSの利用徹底や再試行設定の見直しなど、Canonicalが示した緩和策を組み合わせて講じることで、修正適用までの間のリスクを抑えることができる。
