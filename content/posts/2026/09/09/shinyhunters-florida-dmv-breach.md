---
date: "2026-09-09T18:14:32+09:00"
title: "ShinyHuntersがフロリダ州DMVデータベース「DAVID」侵入を主張、パスワードリセットの欠陥でFBI捜査官のアカウントも侵害"
description: "恐喝グループShinyHuntersが、フロリダ州運輸安全・自動車局の運転免許・車両情報データベース「DAVID」から20万件超の記録を窃取したと主張し、9月11日までの交渉がなければ流出させると脅迫している。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/shinyhunters-hackers-claim-breach-of-florida-david-dmv-database/"
  - "https://cyberinsider.com/shinyhunters-claims-breach-of-florida-dmv-threatens-data-leak/"
  - "https://cybernews.com/privacy/shinyhunters-claim-florida-dmv-jeffrey-epstein/"
---

## 概要

恐喝グループShinyHuntersが、フロリダ州運輸安全・自動車局(FLHSMV)が運用する運転免許・車両情報データベース「DAVID」(Driver and Vehicle Information Database)への侵入を主張し、20万件超の記録を窃取したとリークサイト上で公表した。同グループは9月7日にこの侵害を掲載し、9月11日までにFLHSMVが交渉に応じなければ、盗んだとするデータを公開すると脅迫している。CyberInsiderによると、9月8日時点でFLHSMVはこの主張について公式な確認を出していない。

## 侵入の手口と証拠として公開されたデータ

ShinyHuntersがBleepingComputerに語った内容によれば、侵入経路はパスワードリセット機能の欠陥だったという。この欠陥を悪用してDMV職員および州の自動車ポータルにアクセス権を持つFBI捜査官のアカウントを乗っ取り、DAVIDへの正規アクセス権限を獲得したと主張している。DAVIDには運転免許申請情報、顔写真、署名、住所、車両履歴、保険情報などが格納されており、法執行機関や州職員がドライバー情報を照会する際に利用するシステムである。

侵害の証拠として、同グループはジェフリー・エプスタインの運転免許記録とされるスクリーンショットを公開した。この記録には住所、社会保障番号、生年月日、運転免許ID、発行・有効期限日、登録車両情報まで含まれていたとされる。ただし、CyberInsiderをはじめとする報道各社は、表示された記録の真正性やデータがFLHSMVからの直接的な侵害によるものかを独自に検証できていないとしている。

## 対応状況と今後の見通し

ShinyHuntersは、FLHSMVがこれまで交渉に応じていないと主張しており、9月11日の期限を過ぎた場合はデータの公開に踏み切る構えを見せている。FLHSMV側からの公式な侵害確認は本稿執筆時点で出されておらず、実際の被害範囲や侵害の事実関係は依然として不透明だ。なお、この一件は過去にIDScan.netから運転免許スキャン画像1億5,300万件が流出した事案とは無関係の、別の侵害主張である点に注意が必要となる。ShinyHuntersは近年、大手企業や公共機関を狙った同種の恐喝キャンペーンを繰り返しており、今回も同様の手口で身代金や交渉を引き出そうとしている可能性が高い。
