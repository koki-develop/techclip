---
date: "2026-11-13T08:07:05+09:00"
title: "Microsoft 365で世界的大規模障害、Outlook・Teams・Copilotに加えAIコネクタも連鎖的に機能停止"
description: "Microsoftのクラウド基盤で大規模障害が発生し、Outlook・Teams・Copilotなどが世界的に利用不能となり、OpenAIやAnthropicのAIコネクタにも影響が及んだ。"
tags:
  - Cloud
references:
  - "https://www.bleepingcomputer.com/news/microsoft/massive-microsoft-365-outage-disrupts-outlook-teams-copilot-worldwide/"
  - "https://securityaffairs.com/202932/security/microsoft-cloud-outage-hits-outlook-teams-copilot-and-ai-services.html"
  - "https://www.euronews.com/2026/11/12/microsoft-outage-hits-outlook-teams-and-copilot-disrupting-thousands"
---

## 概要

2026年11月12日、Microsoftのクラウド基盤で世界的な大規模障害が発生し、Outlook、Teams、Copilot、Exchange Online、SharePoint Online、OneDrive、Microsoft Defender XDR、Microsoft Storeなど広範なサービスに接続できない状態が続いた。障害は米東部時間午後1時26分頃に本格化し、Downdetectorには数時間でOutlookが9万7000件超（報道によっては13万件超）、Microsoft 365が3万8000〜4万6000件超の障害報告が寄せられた。これとは別に、同日午前9時45分から10時53分(ET)にかけてTeamsでもリソース競合によるメッセージ遅延・送受信失敗が発生しており、両者は独立したインシデントとされる。影響は当初アメリカ大陸で特に深刻だったが、Microsoftは後に「どの地域のユーザーでも影響を受ける可能性がある」ことを認めた。

## 原因と連鎖の構造

Microsoftは当初、複数リージョンにわたる「インフラ負荷の上昇」が原因と説明していたが、その後X(旧Twitter)上で説明を修正し、「負荷上昇はトラフィックの増加によるものではなく、一部のサーバーが予期せず利用不能になったことで、残りの基盤に負荷が集中したため」と原因を改めた。記事によれば、サーバー群が自動ヘルスチェックに失敗して脱落し、生き残ったサーバーに処理が集中するカスケード障害(将棋倒し的な負荷集中)が発生した構図だ。Microsoftはサイバー攻撃を示す証拠はないとしている。対応としては、新規デプロイメントの一時停止、トラフィックの世界規模インフラへの再分配、影響システムからの負荷移動、利用不能になったサーバーの再起動による容量回復を進め、「影響を軽減するためあらゆる手段を積極的に追求している」と述べた。

## AIサービスへの波及

今回の障害で注目されたのは、Microsoft自身のCopilotだけでなく、OpenAIやAnthropicが提供するAIコネクタにも障害が連鎖した点だ。これらのコネクタはユーザーがOutlookなど自身のMicrosoft 365アカウントにAIアシスタントからアクセスできるようにする機能で、Copilotや競合AIツールがメールボックスへ接続するための基盤をMicrosoft側のサービスが支えている。今回はその基盤自体が落ちたため、接続機能そのものが無効化される形となり、クラウド基盤への依存が特定ベンダーの一社にとどまらず、競合を含むAI生態系全体に及ぶことが明らかになった。

## 復旧状況と今後の影響

Microsoftは北米でのTeamsの問題については解決を報告したものの、一部ユーザーでは依然として不具合が続いていたとされる。報道時点ではOutlookを含む大規模障害自体は未解決で、IT管理者はMicrosoft 365管理センターで最新状況を確認するよう案内されていた。企業の基幹業務がメールやチャット、AIアシスタントまで単一クラウド事業者に集中する現状において、一部サーバーの自動ヘルスチェック失敗という比較的限定的な引き金が、世界規模かつ複数サービス・複数ベンダーへの連鎖的な機能停止に発展した今回の事例は、可用性設計や冗長化のあり方を問うものとなった。
