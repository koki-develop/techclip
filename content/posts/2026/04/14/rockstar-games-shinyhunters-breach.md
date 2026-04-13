---
date: "2026-04-14T02:30:55+09:00"
title: "ShinyHuntersがSaaS「Anodot」経由でRockstar GamesのSnowflake環境に侵入、身代金を要求"
description: "ハッカー集団ShinyHuntersがクラウドコスト管理SaaS「Anodot」を踏み台にRockstar GamesのSnowflakeデータへ不正アクセスしたと主張し、4月14日を期限とした身代金要求を行った。Rockstar Gamesはサードパーティ経由のデータ侵害を公式に認めたが、詳細は明らかにしていない。"
tags:
  - Security
references:
  - "https://www.theregister.com/2026/04/13/shinyhunters_rockstar_breach/"
  - "https://www.helpnetsecurity.com/2026/04/13/rockstar-games-data-breach-shinyhunters/"
  - "https://www.engadget.com/cybersecurity/rockstar-games-has-confirmed-it-was-hit-by-third-party-data-breach-175112621.html"
---

## 概要

Rockstar Gamesは2026年4月11日、サードパーティのデータ侵害により「限定的な非重要な社内情報」が不正アクセスされたことを公式に認めた。攻撃を主張するのはハッカー集団ShinyHuntersで、同グループはSaaS型クラウドコスト管理・分析ツール「Anodot」を足がかりにRockstar GamesのSnowflakeデータウェアハウス環境へ侵入したと主張している。4月11日には「Rockstar Games! AnodotによってSnowflakeインスタンスが侵害された。支払うか、データを公開するか」というメッセージをダークウェブのリークサイトに投稿し、4月14日を支払期限とした身代金要求を突きつけた。Rockstar Gamesは「プレイヤーのデータや事業運営への影響はない」としているが、具体的にどのようなデータが流出したかは明らかにしていない。

## 攻撃手法：SaaS連携を悪用したサプライチェーン型侵害

今回の攻撃で注目されるのは、Snowflake自体の脆弱性を突くのではなく、Snowflakeと連携するサードパーティSaaSを踏み台にした点だ。ShinyHuntersはAnodotからSnowflakeへの接続に使用する認証トークンを入手し、正規の内部サービスになりすましてSnowflakeのデータにアクセスしたとされる。Anodotでは4月4日に複数リージョンでSnowflake・Amazon S3・Amazon Kinesis連携のコネクタ障害が発生しており、この障害がトークン窃取と関連している可能性が指摘されている。ShinyHuntersはAPIやアイデンティティシステム、SaaS連携を標的にする手法を得意とし、従来のネットワーク境界防御では検出しにくい攻撃を行うことで知られている。

## ShinyHuntersの背景と過去の被害実績

ShinyHuntersは高知名度のテック企業や大規模サービスを繰り返し標的にしてきた集団で、過去にはCisco、Telus、欧州委員会、Aura、Salesforceなどへの侵害を主張している。また、Microsoft、Google、Ticketmasterといった企業も被害を受けたと報じられている。一方Rockstar Gamesにとっては今回が2度目の大規模セキュリティインシデントとなる。2022年には別のハッカー集団Lapsus$（当時18歳のメンバー）がSlackへ侵入し、開発中の「Grand Theft Auto VI」のゲームプレイ映像と開発資産を大量に流出させた。この攻撃者は後に無期限入院処分を受けている。

## 今後の懸念とセキュリティへの示唆

Rockstar Gamesは4月14日の身代金期限に対して公式には応答していない。「非重要な情報のみ」としているものの、Snowflakeに格納されていたメトリクスデータの詳細は依然として不明だ。今回の事案は、クラウドサービス間の連携に潜むセキュリティリスク、特にSaaS製品が保有する認証情報の管理の重要性を改めて浮き彫りにしている。最小権限の原則に基づくアクセス制御の徹底や、サードパーティ連携の定期的な監査がこうした攻撃への対策として不可欠であることを示す事例といえる。
