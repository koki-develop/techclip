---
date: "2026-11-25T08:07:06+09:00"
title: "CISA、ランサムウェアやクリプトマイニング、LLMjackingに悪用される4件の脆弱性をKEVカタログに追加"
description: "CISAがApache Axis、REDCap、LiteLLM、Synology DSMの4件の脆弱性を既知の悪用済みカタログに追加し、連邦機関に11月21日または12月2日までの対応を義務付けた。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/11/cisa-warns-of-4-exploited-flaws-linked.html"
  - "https://securityaffairs.com/203504/hacking/u-s-cisa-adds-apache-axis-vanderbilt-redcapberriai-litellm-and-synology-dsm-flaws-to-its-known-exploited-vulnerabilities-catalog.html"
---

## 概要

米CISA(サイバーセキュリティ・インフラセキュリティ庁)は11月18日、Apache Axis、Vanderbilt REDCap、BerriAI LiteLLM、Synology DSMの4件の脆弱性を既知の悪用済み脆弱性(KEV)カタログに追加した。いずれも実環境で悪用が確認されており、攻撃内容はランサムウェア配布、クリプトマイニング、AIサービスの認証情報を乗っ取る「LLMjacking」まで多岐にわたる。連邦機関にはBinding Operational Directive 22-01に基づき、Synology DSM・REDCap・Axisの3件は11月21日まで、LiteLLMは12月2日までの対応が義務付けられた。

## 4件の脆弱性の詳細

最も深刻度が高いのはApache Axisの「CVE-2026-90436」(CVSS 9.8)で、安全でないリフレクション処理により未認証の攻撃者が任意のコードを実行できる。Rapid7の分析によると、攻撃者はAtlassian Confluence Data Center上でこの脆弱性を突き、PinggyやCloudflare Tunnelの一時ドメインから取得したシェルコマンドやスクリプトを実行し、わずか数分でデータベースから認証情報やトークン、VPN設定を窃取、本番のクラウドデータウェアハウスにもアクセスしていた。Axis 1.xは既にEnd-of-Lifeを迎えており公式パッチは提供されないため、CISAはAxis 2/Javaへの移行、または2026年7月12日付のコミットで提供されたパッチの適用を推奨している。

Vanderbilt REDCapの「CVE-2026-90817」(CVSS 9.8)はコード注入の脆弱性で、有効な公開サーベイのハッシュ値を知っていれば未認証でも任意コードを実行できる。Safe Securityの調査では、攻撃者はこの脆弱性を使ってWebシェルを設置し、画像ファイルや正規のプロセスに偽装したXMRigマイニングマルウェアを展開、cronジョブやSSH鍵を通じて持続的なアクセスを確保していたことが確認されている。

Synology DSMの「CVE-2024-10441」(CVSS 9.8)は出力のエンコーディング・エスケープ処理が不適切な脆弱性で、NAS(ネットワーク接続ストレージ)デバイスを狙ったランサムウェア攻撃に悪用され、「C3RB3R」ランサムウェアの配布に使われている。データ損失につながる実害が報告されている。

## LLMjackingに悪用されるLiteLLMの脆弱性

BerriAI LiteLLMの「CVE-2026-40217」(CVSS 8.8)は保護されていない代替チャネルの脆弱性で、`/guardrails/test_custom_code`というURIエンドポイント経由で悪用可能。この脆弱性を突かれると、本来は推論用途に限定されたAPIキーが管理者権限相当の認証情報へと昇格してしまう。Googleの脅威インテリジェンスグループ(GTIG)は、この脆弱性を使ったLLMjacking攻撃が北米、南米、アジア太平洋地域の金融、小売、運輸、技術分野の組織を標的にしていると報告しており、攻撃者は昇格した管理者権限を使って持続的なアクセスを確立していた。LLMjackingは窃取・乗っ取ったAI推論サービスの認証情報を悪用し、攻撃者が不正に大規模言語モデルへのアクセスを得て高額な利用料を発生させたり、他の攻撃基盤として利用したりする手口で、近年AIサービスの普及に伴い増加している攻撃形態の一つである。

## 今後の対応

今回のKEVカタログ追加は、ソフトウェアサプライチェーンの広がりにより、レガシーなJavaライブラリからNAS機器、医療・学術分野で広く使われるREDCapのようなWebアプリケーション、さらには新興のAI推論基盤までが同時に攻撃対象となっている実態を示している。特にAxis 1.xのようにEOLを迎えて公式サポートが打ち切られたソフトウェアが現役の攻撃経路として使われ続けている点、またLiteLLMのようなAI関連インフラが新たな攻撃対象として急速に狙われ始めている点は注意が必要だ。連邦機関以外の組織においても、該当するソフトウェアを利用している場合は期限を待たず速やかなパッチ適用や緩和策の実施が強く推奨される。
