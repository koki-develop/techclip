---
date: "2026-11-11T08:06:53+09:00"
title: "Microsoft、11月のPatch Tuesdayで1,000件超の脆弱性を修正、悪用済みOutlookゼロデイはNTLMハッシュ窃取に悪用"
description: "Microsoftが2026年11月の月例更新で1,000件超の脆弱性を修正し、実際に悪用されていたOutlookのゼロデイ脆弱性CVE-2026-124194を含む修正をCISAが既知の悪用脆弱性カタログに追加した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-november-2026-patch-tuesday-fixes-1-235-flaws-outlook-zero-day/"
  - "https://www.securityweek.com/exploited-outlook-zero-day-among-1094-flaws-patched-by-microsoft/"
  - "https://cyberscoop.com/microsoft-patch-tuesday-november-2026/"
---

## 概要

Microsoftは11月の月例セキュリティ更新「Patch Tuesday」で、1,000件を超える脆弱性を修正した。件数は報道によって1,094件から1,235件までばらつきがあるが、これは正式にCVE番号が割り当てられた脆弱性の数え方や、サードパーティ製コンポーネントの再掲載分を含めるかどうかの違いによるものとみられる。いずれにせよ、10月の過去最多記録(1,411〜1,413件)に次ぐ規模であり、年間の修正件数は既に5,000件を超えている。内訳では、Windows関連が726件、Officeが174件、SQL Serverが59件、開発者向けツールが53件、SharePoint Serverが27件、Azureが20件、Exchange Serverが9件などとなっており、サードパーティCVEの再掲載分も165件含まれている。深刻度では、Remote Code Execution(RCE)やElevation of Privilege(EoP)に分類される脆弱性が大部分を占め、Microsoft Edge(Chromium版)関連の修正も142件にのぼった。

## 悪用済みのOutlookゼロデイ

今回の修正で最も注目されたのが、既に実際の攻撃で悪用されていたOutlookのスプーフィング脆弱性CVE-2026-124194だ。CVSSスコアは6.5で「中程度」の深刻度に分類されているものの、実害は小さくない。攻撃者は特別に加工したメッセージファイルを送り、ユーザーがこれを開くと、Outlookが通常表示される「外部コンテンツ」の警告なしに、攻撃者が管理する外部サーバーへ接続してしまう。このとき、Windowsが自動的に認証を試みることで、ユーザーのNTLMv2認証ハッシュが外部に流出する。流出したハッシュはオフラインでのクラック解析や、被害者になりすましたアカウント侵害に利用され得る。プレビューウィンドウでは発火しないため悪意あるファイルを明示的に開く操作が必要だが、攻撃は既に確認されており、CISAはこの脆弱性を既知の悪用脆弱性(KEV)カタログに追加し、連邦政府機関に対して11月24日までの対応を義務付けた。脆弱性はMicrosoft 365 Apps for EnterpriseやOffice LTSC 2021/2024に影響し、研究者「nono」とBenoît Sevens氏(Anthropic社のClaudeモデルを活用した調査で貢献したとされる)が報告したことが明らかになっている。

## その他の注目すべき脆弱性

Outlookのゼロデイ以外にも、深刻な脆弱性が複数修正された。Exchange Server経由で到達可能なWindows検索の脆弱性CVE-2026-116928は、価値の高い標的に対する「ゼロクリックのコード実行」バグとして位置付けられている。また、CVSSスコア9.8という最高レベルの深刻度を持つWindows LDAPの脆弱性も修正されており、特にドメインコントローラーにおいて大きな被害をもたらす可能性が指摘されている。TrendAI傘下のZero Day Initiativeのダスティン・チャイルズ(Dustin Childs)氏は、今回の規模について「これは好ましい傾向だが、実際の悪用が減っているわけではない」と指摘し、AIによる修正の解析能力が向上することで、攻撃者側の手法も変化していく可能性があるとの見方を示した。

## 今後の対応

Outlookのゼロデイが既に実際の攻撃に使われていたこと、またWindows検索やLDAPに深刻度の高い脆弱性が見つかったことから、企業や組織は優先的にこれらの修正を適用する必要がある。特にCISAのKEVカタログ入りした脆弱性は連邦機関に明確な対応期限が設定されており、民間組織にとっても事実上の目安となる。月次の修正件数が1,000件を超える状況が続く中、AIを活用した脆弱性発見・修正のスピードが上がる一方で、攻撃側の解析・悪用のスピードも追随しているとの指摘もあり、パッチ適用の迅速化がこれまで以上に重要になっている。
