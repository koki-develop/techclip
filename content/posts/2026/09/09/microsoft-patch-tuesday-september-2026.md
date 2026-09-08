---
date: "2026-09-09T08:11:16+09:00"
title: "Microsoftが2026年9月Patch Tuesdayで過去最多970件超の脆弱性を修正、悪用済みゼロデイ2件にCISAが対応期限"
description: "Microsoftが2026年9月のPatch Tuesdayで過去最大規模となる約970件の脆弱性を修正し、実際に悪用が確認されているゼロデイ2件についてCISAが連邦機関に9月22日までの対応を求めた。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-september-2026-patch-tuesday-fixes-966-flaws-2-zero-days/"
  - "https://www.securityweek.com/microsoft-patches-record-974-vulnerabilities-including-two-exploited-zero-days/"
  - "https://therecord.media/microsoft-patch-tuesday-september-2026"
---

## 概要

Microsoftは9月の月例セキュリティ更新(Patch Tuesday)で、過去最大規模となる脆弱性の修正を公開した。件数は報道元によって966件から974件までばらつきがあるが、いずれにせよ月間の修正件数として900件の大台を初めて超えた計算になる。2026年の年間累計修正件数はすでに2,600件を突破しており、これまでの記録だった2020年の約2倍のペースだという。今回のリリースで特に注目されるのは、実際の攻撃で悪用が確認されているゼロデイ脆弱性が2件含まれている点で、CISA(米サイバーセキュリティ・インフラセキュリティ庁)は連邦機関に対し9月22日までの対応を義務付けている。

内訳を見ると、Windows関連が723件と全体の大半を占め、Officeスイートが222件(うちOffice 2016単体で111件)、SQL Serverが62件、開発者ツールが22件、SharePoint Serverが16件、Azureが12件、Skype for Businessが10件、Exchange Serverが9件と続く。深刻度別ではCritical(緊急)評価が105件におよび、このうちリモートコード実行(RCE)が81件、権限昇格が20件を占める。全体でもRCEが258件、権限昇格が438件と多数を占めており、認証やユーザー操作なしに悪用可能な「ワーム化可能」な脆弱性も20件含まれているとされる。

## 悪用済みゼロデイの詳細

1件目のCVE-2026-81963は、Windows Update Stackにおける権限昇格の脆弱性で、ファイルアクセス前のリンク解決を適切に処理していないことが原因とされる。攻撃者はこれを悪用してSYSTEM権限を取得できる。Windows Update Stackでゼロデイが報告されるのは過去5年間で初めてであり、更新の仕組みそのものを制御する経路が突かれた点で影響が大きいとの指摘がある。発見はMicrosoft Threat Intelligence Centre(MSTIC)のRomain Deperne氏によるものだ。

2件目のCVE-2026-85880は、Windows ALPC(Advanced Local Procedure Call)におけるヒープベースのバッファオーバーフローで、こちらも悪用によりSYSTEM権限への昇格が可能となる。低権限のAppContainerサンドボックス内で実行されるコードを持つ攻撃者が、サンドボックスをエスケープする手段として悪用できるとされ、ALPC関連のゼロデイとしては2023年1月以来2番目の事例となる。発見にはVolexity、Mark Kelly氏、David Galazin氏、およびProofpointのJeremy Hedges氏が関わったと報告されている。両脆弱性とも権限昇格にとどまり単独でのリモート侵入には使えないが、フィッシングなどで初期アクセスを得た攻撃者が権限を拡大する段階で悪用される典型的な組み合わせとされ、CISAはこの2件を既知の悪用脆弱性(KEV)カタログに追加した。

## その他の注目すべき脆弱性

ゼロデイ以外にもCritical評価の脆弱性が多数含まれる。Graphics Fontsの解析処理に起因するRCE(CVE-2026-72986、CVE-2026-73018)、IP HelperサービスのRCE(CVE-2026-72981)のほか、Excel・Outlook・PowerPoint・Wordといった主要Officeアプリケーションにも複数のCritical RCEが存在する。セキュリティ研究者のDustin Childs氏は、Exchange ServerのRCE(CVE-2026-55007)、Microsoft Authenticatorの権限昇格(CVE-2026-80097)、SharePointのRCE(CVE-2026-69465)、Remote Desktop ServicesのRCE(CVE-2026-69525)を優先対応すべき脆弱性として挙げている。特にExchange ServerやSharePoint Serverはインターネットに公開されるケースが多く、企業のメールやドキュメント基盤に直結するため注意が必要だ。

## 件数急増の背景と専門家の見解

今回の修正件数の急増は、Microsoftが脆弱性発見にAIを活用する取り組みを進めていることが一因とされる。直近の月別件数は7月が570件、8月が400件だったのに対し、9月は966件前後まで跳ね上がった。もっともTenableのSatnam Narang氏は、「脆弱性の絶対数は増えているが、実際に大多数の組織へ影響する脆弱性の数はさほど変わらない。AI支援による発見は『干し草の山』を大きくしているだけで、必ずしも『針』を多く見つけているわけではない」と指摘する。一方でFortraのTyler Reguly氏は、大量のパッチ公開は「ベンダーが攻撃対象領域を積極的に縮小しようとしている表れ」だとしつつ、管理者にはリスクの実態に基づいた優先順位付けが不可欠だと強調している。件数の膨張が続く中、まずはゼロデイとCritical評価のRCE・権限昇格から適用を進め、インターネットに露出したExchangeやSharePointなどの基盤を優先的に検証することが求められる。
