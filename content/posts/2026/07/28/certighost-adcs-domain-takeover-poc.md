---
date: "2026-07-28T02:35:15+09:00"
title: "AD CSの重大脆弱性「Certighost」、低権限ユーザーがDC乗っ取り可能なPoCコードが公開"
description: "Active Directory証明書サービスの脆弱性CVE-2026-54121(通称Certighost)を突き、低権限ドメインユーザーがドメインコントローラーになりすましkrbtgtハッシュを窃取できる概念実証コードが公開された。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/07/certighost-exploit-lets-low-privileged.html"
  - "https://cybersecuritynews.com/certighost-active-directory-cs-flaw/"
  - "https://www.helpnetsecurity.com/2026/07/27/certighost-cve-2026-54121-poc-exploit-released/"
---

## 概要

Active Directory証明書サービス(AD CS)に存在する認可不備の脆弱性「Certighost」(CVE-2026-54121、CVSSスコア8.8)を悪用し、低権限のドメインユーザーがドメインコントローラー(DC)になりすませる概念実証(PoC)コードが2026年7月下旬に公開された。この脆弱性を突けば、攻撃者はDCとして証明書認証を成立させたうえでDCSync攻撃を実行し、Kerberos認証の要であるkrbtgtアカウントのシークレットを窃取できる。krbtgtハッシュが奪われればゴールデンチケットの偽造が可能となり、事実上ドメイン全体の恒久的な侵害につながる。研究者からMicrosoftへは2026年5月に責任ある開示が行われ、Microsoftは同年7月14日付の月例更新で修正を提供済みだが、その2週間ほど後にPoCが一般公開されたことで悪用リスクが急速に高まっている。現時点で実際の悪用は確認されていないという。

## 技術的な詳細

Certighostは、AD CSがクロスドメインコントローラー登録シナリオで備えている「チェース(chase)」と呼ばれるフォールバック機能を悪用する。証明書登録要求の際、攻撃者は`cdc`(Client DC、接続先ホストを指定)と`rmd`(Remote Domain、参照先プリンシパルを指定)という2つの属性をリクエストに挿入できる。本来、認証局(CA)はこれらの属性で指定されたホストが実在の正規DCであることを検証すべきだが、この検証処理が欠落していた。

具体的な攻撃手順は次の通りである。まず攻撃者は、既定の`ms-DS-MachineAccountQuota`設定(一般ユーザーでも最大10台までマシンアカウントを追加登録できる)を利用して自身が制御するマシンアカウントを作成する。次に、そのマシン上で不正なSMB・LDAP・LSAサービスを起動し、CAからの認証チャレンジをNetlogon経由で実際のDCへリレーする。これにより本物のDCの`objectSid`と`dNSHostName`を取得し、CAに対してあたかも正規DCであるかのように証明書要求を完了させる。発行された証明書はPKINITによるKerberosチケット取得に使用でき、最終的にDCとして認められた権限で複製権(ディレクトリレプリケーション権)を行使し、DCSyncによってkrbtgtの秘密情報を抽出する。影響範囲はWindows Server 2012からWindows Server 2025(Core版含む)、およびWindows 10バージョン1607・1809まで幅広く、Enterprise CAの構成が前提条件となる。この脆弱性は複数のセキュリティ研究者(H0j3n氏、Aniq Fakhrul氏、Muhammad Ali氏ら)によって発見され、2026年5月14日にMicrosoftへ報告、5月22日に確認された。

## 対応と緩和策

Microsoftは7月の月例更新で、`certpdef.dll`内に新たな検証関数`_ValidateChaseTargetIsDC`を追加する形で修正を行った。この関数は、空文字列や過度に長い名前、IPアドレス形式の指定、LDAPインジェクションに利用され得る制御文字を含むホスト名を拒否するほか、DNS名の完全一致確認と`SERVER_TRUST_ACCOUNT`フラグの検証によって、指定されたホストが実際に正規のマシンオブジェクトであることを確認する仕組みを備える。

パッチを直ちに適用できない環境向けには、レジストリ経由でチェース機能自体を無効化する一時的な緩和策も提示されている。具体的には`certutil -setreg policy\EditFlags -EDITF_ENABLECHASECLIENTDC`を実行し、証明書サービス(CertSvc)を再起動する方法だが、Microsoft自身もこれは正規の登録フローに影響を及ぼしうる暫定措置に過ぎないとしており、恒久的な対策としてはセキュリティ更新プログラムの適用が推奨される。PoCが一般公開された今、AD CSを運用する組織は速やかなパッチ適用状況の確認と、DC乗っ取りを想定した監視体制の強化が求められる。
