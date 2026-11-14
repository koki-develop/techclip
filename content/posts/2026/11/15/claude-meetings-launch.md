---
date: "2026-11-15T08:06:47+09:00"
title: "Anthropicが「Claude Meetings」を発表、会議参加から議事録・タスク化までAIが代行"
description: "AnthropicがGoogle Meet向け会議参加AI「Claude Meetings」をベータ公開し、ホワイトボードやスプレッドシートなどの新機能も同時投入した。"
tags:
  - AI
references:
  - "https://techcrunch.com/2026/11/10/anthropic-launches-claude-meetings-to-turn-workplace-discussions-into-plans-and-tasks/"
  - "https://www.techradar.com/pro/claude-can-now-join-your-weekly-meeting-to-take-notes-and-even-start-work-for-you-and-thats-not-all-with-new-spreadsheet-whiteboard-tools-and-more-helping-conquer-the-world-of-frontier-work"
  - "https://dataconomy.com/2026/11/13/anthropic-brings-claude-meetings-to-google-meet-in-beta/"
---

## 概要

Anthropicは11月10日、会議にAIを参加者として招き入れる新機能「Claude Meetings」を発表した。Google Meetの通話にClaudeがボットではなく参加者として加わり、議論の内容をリアルタイムで要約し、計画やタスクに変換する。同時に「Claude Whiteboards」「Claude Sheets」という2つの新しいコラボレーションツール、そしてAdobe・Atlassian・HubSpotと連携する新しいコネクタ群も投入された。これらはTeam/Enterpriseプランを中心にベータ提供が始まっており、OpenAIやMetaが進める「AIオフィススイート」競争に対するAnthropicの回答という位置づけになる。

## Claude Meetingsの仕組みとプライバシー設計

Claude Meetingsは会議中、チャットでの質問への応答、タイムラインの作成、連携済みの業務アプリからのデータ取得をリアルタイムで行う。単に裏側で記録するのではなく、会議チャットに参加通知を投稿するなど、自らの存在を明示する設計になっている点が特徴だ。プライバシー面では、管理者の許可がない外部ゲストが会議に参加した場合は自動的に退出する仕組みを備えている。まずはGoogle Meetでのベータ提供から始まり、今後他のビデオ会議プラットフォームへの対応拡大が予定されている。

## ホワイトボード・スプレッドシートと新コネクタ

同時発表された「Claude Whiteboards」は、口頭でのブレインストーミングや整理されていない議論を、担当者や期日付きのタイムラインを持つ共同編集可能なボードへと変換する機能で、完成したボードはドキュメントやスライドにも書き出せる。「Claude Sheets」はプロンプトから複数タブ・数式・書式・ドロップダウンメニューを備えた実用的なスプレッドシートを生成し、チームメンバーと共同編集できる。両機能はWeb・デスクトップ・モバイルの有料プランでベータ提供される。さらに、データウェアハウスやCRMへの接続機能だった「Claude Dashboards」は「Claude Data」に改称されて一般提供(GA)に移行し、Adobe・Atlassian・HubSpotとの対話型コネクタも新たに追加された。

## 展望

今回の発表は、AnthropicがChatGPTやMetaのAIアシスタントと同様に、単なる対話型AIから「職場の実務を代行するエージェント」への拡張を急いでいることを示している。会議への参加、ホワイトボードでの発想整理、スプレッドシート作成という一連の業務フローをClaudeが橋渡しすることで、議事録作成やタスク化といった定型作業の自動化が進むと見られる。一方で、外部ゲスト参加時の自動退出のようなガバナンス機能が今後の企業導入の評価軸になりそうで、Google Meetでのベータでどこまで実用に耐えるかが当面の注目点となる。
