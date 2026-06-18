---
date: "2026-06-19T03:04:13+09:00"
title: "「FortiBleed」漏洩：194カ国73,000台以上のFortinetデバイスのVPN認証情報が流出"
description: "「FortiBleed」と呼ばれる大規模なデータ漏洩が発覚し、194カ国にわたる約73,000台以上のFortinetファイアウォールデバイスのVPN認証情報がオンラインで公開されていることが判明した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/fortibleed-leak-exposes-fortinet-vpn-credentials-for-73-000-devices/"
  - "https://www.darkreading.com/cyberattacks-data-breaches/sweeping-credential-harvesting-heist-compromises-30k-fortinet-devices"
---

## 概要

セキュリティ研究者のBob Diachenkoが公開サーバー上に「FortiBleed」と名付けられた大規模な認証情報漏洩を発見した。このデータセットには194カ国にわたる約73,932台のFortinetファイアウォールに対応するURLが含まれており、ユーザー名・メールアドレス・平文パスワードを含む有効なFortigate VPN認証情報が記録されていた。これはインターネット上にアクセス可能な全FortiGateデバイスの約半数に相当し、影響を受けたユニークドメイン数は21,632件に上る。

影響を受けた主な組織には、Chevron・Samsung・Foxconn・Comcast・AT&T・Mercedes-Benz・Toyota・PwC・Accenture・Oracleなどのグローバル大企業に加え、複数の政府機関が含まれている。地理的には、インド・米国・台湾・メキシコ・トルコ・タイ・コロンビア・マレーシア・チリ・UAEが上位の被害国として挙げられている。

## 攻撃手法と流出経緯

研究者らによると、脅威アクターは320,777台のFortiGateターゲットに対して約11.6億回ものクレデンシャル試行を実施した。また、Hashtopolisというソフトウェアで管理された45基のGPUクラスターを使用してSSL VPN認証ハッシュを解読したとされている。流出した認証情報はFortinetの設定ファイルから抽出されたと見られているが、その初期取得方法については依然として不明であり、既知の脆弱性の悪用なのか、未公開の欠陥を突いたものなのか、あるいは別の攻撃ベクターによるものなのかは確認されていない。

## 推奨される対策

影響を受ける可能性のある組織は、以下の対策を速やかに実施することが強く推奨されている。

- **認証情報のローテーション**：Fortinetデバイスに関連するすべてのパスワードを直ちに変更する
- **多要素認証（MFA）の有効化**：VPN接続に対してMFAを設定し、認証情報が漏洩しても不正アクセスを防ぐ
- **ゲートウェイログの精査**：不審なアクセスや認証試行の痕跡がないかログを確認する
- **従業員認証情報の監視**：Hudson Rockの無料ルックアップツール等を活用して、組織の認証情報がデータ漏洩に含まれていないかを確認する

今回の事案は、Fortinetデバイスを含むネットワーク境界機器に対する大規模かつ組織的な認証情報収集キャンペーンが継続していることを改めて示しており、ゼロトラスト原則の実装や特権アクセス管理の強化が急務であることを浮き彫りにしている。
