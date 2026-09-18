---
date: "2026-09-19T08:11:18+09:00"
title: "WooCommerce用プラグインの未修正脆弱性、10万件超の攻撃でPHPウェブシェル設置が横行"
description: "WordPress向け「WooCommerce Wholesale Lead Capture」プラグインの脆弱性CVE-2026-27540が悪用され、未認証の攻撃者がPHPウェブシェルを設置する攻撃が10万件以上検知された。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/09/attackers-exploit-woocommerce-wholesale.html"
  - "https://www.bleepingcomputer.com/news/security/hackers-target-wordpress-sites-via-third-party-woocommerce-plugin/"
  - "https://www.infosecurity-magazine.com/news/woocommerce-wholesale-lead-capture/"
---

## 概要

Rymera Web Co提供のWordPress向けプラグイン「WooCommerce Wholesale Lead Capture」に存在する未認証ファイルアップロードの脆弱性(CVE-2026-27540、Wordfence評価でCVSS 9.8、Patchstack評価では9.0)が悪用され、攻撃者がPHP製ウェブシェルを設置する攻撃が急拡大している。同プラグインは6,000件以上のサイトで稼働しており、セキュリティ企業Wordfenceは今年6月以降だけで10万件超の攻撃を検知したと報告した。攻撃のピークは6月4日から17日にかけて、また7月1日と8月30日にも急増が観測されている。パッチはすでに2月20日リリースのバージョン2.0.3.2で提供済みだが、約4か月が経過した現在も多数のサイトが未更新のまま被害に遭っている。

## 技術的な詳細

脆弱性の本質は、卸売登録フォームのファイルアップロードを処理するAJAXアクション「wwlc_file_upload_handler」にある。本来はサーバー側の設定で許可ファイル形式を管理すべきところ、ユーザーが送信するリクエストパラメータ「file_settings」からその許可リストを直接読み込んでしまう実装上の欠陥があり、攻撃者はこのパラメータを改ざんして「php」を許可拡張子リストに追加できてしまう。これにより未認証のままでも、細工したリクエストと「shell.php」といった名前の悪意あるPHPファイルを送信するだけでサーバー上にウェブシェルを設置できる。設置されたウェブシェルはホスト情報を攻撃者に送信し、さらなる悪意あるファイルを追加アップロードできるブラウザベースのフォームを提供する仕組みになっている。脆弱性を発見したのはセキュリティ研究者のTeemu Saarentaus氏で、影響を受けるのはバージョン2.0.3.1以下のすべてのリリースとなる。

## 攻撃の規模と対応

Wordfenceのファイアウォールはこれまでに10万件を超える悪用の試みをブロックしており、直近24時間だけでも99件の攻撃を記録した。攻撃元は複数のIPアドレスから確認されており、Wordfenceは代表的な発信元IPアドレスのリストを公開している。管理者への推奨対応としては、プラグインを直ちにバージョン2.0.3.2以降へ更新するとともに、アップロードディレクトリ内の予期しないPHPファイルの有無を確認し、「/wp-admin/admin-ajax.php」に対する「wwlc_file_upload_handler」アクションを含む不審なリクエストがないかサーバーログを精査することが挙げられる。侵害が確認された場合は、不正な管理者アカウントやバックドアの削除、あるいはクリーンなバックアップからの復元が必要になる。

## 背景と展望

WordPressのプラグインエコシステムを狙った同種の攻撃は今回に限らない。The Hacker Newsは、60万サイト以上で利用される「The Events Calendar」プラグインでも同様に深刻な脆弱性(CVE-2026-78159、CVE-2026-78006)が発見され、開発元StellarWPがバージョン6.17.3.1および6.17.4.1で修正した事例を伝えている。パッチ公開から数か月が経過してもなお大規模な悪用が続く今回のケースは、サードパーティ製プラグインの更新遅延がWordPressサイト運営における恒常的なリスクであることを改めて示しており、管理者にはプラグインの棚卸しと迅速なパッチ適用の徹底が求められる。
