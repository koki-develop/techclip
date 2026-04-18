---
date: "2026-04-18T18:14:53+09:00"
title: "教育大手McGraw Hill、Salesforce設定ミスでShinyHuntersに1,350万件のデータ流出"
description: "ハッカー集団ShinyHuntersがMcGraw HillのSalesforce環境の設定ミスを悪用し、氏名・住所・電話番号・メールアドレスを含む1,350万件超のユーザーデータを窃取・公開した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/data-breach-at-edtech-giant-mcgraw-hill-affects-135-million-accounts/"
  - "https://www.theregister.com/2026/04/16/mcgraw_hill_salesforce/"
---

## 概要

教育コンテンツ大手のMcGraw Hillが大規模なデータ漏洩被害を受けたことが明らかになった。ハッカー集団ShinyHuntersが同社のSalesforce環境における設定ミスを悪用し、1,350万件のユーザーアカウントデータを窃取。100GB超のデータがダークウェブのリークサイトに公開された。流出したデータには、氏名・住所・電話番号・メールアドレスが含まれており、情報漏洩通知サービス「Have I Been Pwned」でも確認済みとなっている。

## 攻撃手法とShinyHuntersの要求

ShinyHuntersは、Salesforceが連携する環境の設定ミスを起点にMcGraw Hillのシステムへ侵入した。McGraw Hillは「Salesforce環境内の設定ミスに起因するもので、複数の組織が影響を受けた広範な問題の一部」と説明しており、自社固有の脆弱性ではなく連携サービス側の構成問題だと主張している。一般的にSalesforceを介した侵害は、認証情報の窃取、OAuth連携の悪用、過剰な権限が付与されたインテグレーションなどが原因となるケースが多い。

ShinyHuntersは4月14日を身代金支払いの期限として設定し、McGraw Hillがこれに応じなかったことでデータを公開。同グループはダークウェブのリークサイトにRockstar Gamesなど他の被害組織と並べてMcGraw Hillを掲載しており、「4,000万件超のSalesforceレコードを取得した」とも主張している。ただし、McGraw Hillが公表している漏洩件数は1,350万件にとどまっている。

## McGraw Hillの対応と影響範囲

McGraw Hillは今回の侵害について「Salesforceアカウント、コースウェア、顧客データベース、内部システムへの不正アクセスは発生していない」との立場を取り、流出データを「限定的なセット」と位置付けている。しかし、同社は自社のチャンネルでの公式発表をほぼ行わず、報道機関の取材にも回答しないなど、情報開示には消極的な姿勢を示している。

1909年創業で年商22億ドルを誇るMcGraw Hillは、PreK〜12（幼稚園から高校）・高等教育・専門学習向けの教育コンテンツを提供しており、膨大な学習者の個人情報を保有する。流出したメールアドレスや住所等のデータは、スピアフィッシング攻撃などに悪用される可能性があり、被害者となったユーザーへの二次被害が懸念される。

## ShinyHuntersの最近の活動

ShinyHuntersは今回のMcGraw Hill侵害に限らず、欧州委員会、Infinite Campus、Hims & Hers、Panera Bread、SoundCloud、Matchグループが運営する複数のデーティングプラットフォームなど、多数の組織を標的にした攻撃を近年活発化させている。Salesforce連携環境の設定ミスを狙う手口はこのグループの常套手段とも言われており、同様の構成を持つ組織にとっては今回の事例が重大な警鐘となる。
