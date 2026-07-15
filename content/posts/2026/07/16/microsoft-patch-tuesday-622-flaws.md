---
date: "2026-07-16T02:31:33+09:00"
title: "Microsoft、過去最多622件の脆弱性を修正する7月月例パッチを公開、SharePointとAD FSのゼロデイが実悪用中"
description: "Microsoftが史上最多となる622件の脆弱性を修正する2026年7月の月例パッチを公開し、SharePoint ServerとActive Directory Federation Servicesの実悪用中ゼロデイ2件に加え、BitLockerのバイパス問題も明らかになった。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/07/microsoft-patches-record-622-flaws.html"
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-july-2026-patch-tuesday-fixes-massive-570-flaws-3-zero-days/"
  - "https://hackread.com/microsoft-july-2026-patch-tuesday-fixes-zero-days/"
---

## 概要

Microsoftは2026年7月14日、月例セキュリティ更新プログラム「Patch Tuesday」を公開し、史上最多となる622件の脆弱性を修正した（一部報道では570件とも伝えられており、Chromiumベースのコンポーネントの数え方など集計方法の違いによるとみられる）。これは前月6月の約200件の3倍以上にあたる規模で、Windows、Office、SharePoint Server、SQL Server、Azure関連製品、開発者ツールなど広範な製品群が対象となった。とりわけ深刻なのは、SharePoint Server（CVE-2026-56164）とActive Directory Federation Services（AD FS、CVE-2026-56155）における権限昇格の脆弱性2件がすでに実際の攻撃で悪用されている点で、加えてBitLockerのバイパス手法（CVE-2026-50661）も一般に公開済みとなっている。

## 実悪用中のゼロデイの詳細

CVE-2026-56164はSharePoint Serverにおける認証欠如に起因する権限昇格の脆弱性で、CVSSスコアは5.3とされるが、ネットワーク経由で認証情報なしに悪用可能という点が危険視されている。MandiantのインシデントレスポンスチームとGoogle FLAREチームが発見に関与したとされ、影響を受けるSharePoint Server 2016および2019はまさに本更新日にサポート終了（EOS）を迎えており、拡張セキュリティ更新プログラム（ESU）も提供されないため、緩和策としてAMSI（アンチマルウェアスキャンインターフェース）のフルモード有効化が推奨されている。もう一方のCVE-2026-56155はAD FSにおけるアクセス制御の粒度不足に起因する権限昇格の脆弱性で、CVSSスコアは7.8。既に何らかの認証を得た攻撃者がローカルで権限を昇格させる手口とされ、Microsoft社内のインシデント対応部隊DARTが発見に関わったという。このうちAD FSの脆弱性（CVE-2026-56155）は米CISAの既知悪用脆弱性（KEV）カタログに追加されている一方、SharePointの脆弱性（CVE-2026-56164）については記事執筆時点でKEVカタログに未追加と報じられている。これらに加え、物理アクセスを持つ攻撃者がBitLockerによる暗号化を回避できるCVE-2026-50661（CVSS 6.1）も一般公開済みだが、こちらは現時点で実悪用は確認されていない。

## 修正された脆弱性の内訳

今回の更新全体の内訳を見ると、権限昇格が254件と最多を占め、リモートコード実行（RCE）が145件、情報漏えいが102件、サービス拒否（DoS）が35件、セキュリティ機能バイパスが17件、なりすましが16件と続く。深刻度「Critical」に分類された脆弱性は59件にのぼる。製品別ではWindowsが416件と突出して多く、その中にはCVSSスコア9.9と評価されたVMSwitchのRCE（CVE-2026-57092）やDHCP関連のRCE5件が含まれる。ほかにもOfficeが82件、Microsoft Edgeが46件（うちMicrosoft独自の修正は21件、残りはChromium由来の再掲）、SharePoint Serverが17件（Rapid7が報告したJWT認証バイパスのCVE-2026-55040を含む）、開発者ツールが27件（Visual StudioやVS Codeのセキュリティ機能バイパスなど）となっている。なお、SharePointのCVE-2026-55040は別のRCE脆弱性と連鎖させることで未認証のRCEに発展しうるとされるが、そのRCE部分の修正は8月まで持ち越しとなる見込みだ。あわせて、Kerberos認証で脆弱とされるRC4暗号方式について、今回の更新で無効化のロールバックを可能にしていたスイッチ「RC4 DefaultDisablementPhase」が削除された。RC4を使用するレガシーなサービスアカウントが残っている組織は、更新適用前に洗い出しを行い、AESキーを生成させるためのパスワードローテーションを実施しないと認証障害を招く恐れがある。

## 背景と今後の展望

Microsoftは今回の脆弱性件数急増の背景として、複数のAIモデルを組み合わせた社内スキャニングシステム「MDASH」の活用を挙げている。同システムはWindowsのバイナリを検査し、疑わしい脆弱性を自動的にテストする一方、最終的な承認は引き続き人間の専門家が担っているという。600件を超える脆弱性が一度に公開される状況下では、CVSSスコアのみに基づく優先順位付けはもはや不十分との指摘が専門家から相次いでおり、記事内ではCISAのKEVカタログや悪用可能性スコアであるEPSS、Microsoft自身が付与する「悪用済み」フラグを基準に対応の優先順位を決め、迅速にパッチを適用すべきだとの助言がなされている。また別の専門家は、インターネットへの露出度や資産の用途、業務への影響度といった要素も数値スコアと合わせて考慮すべきだと述べている。
