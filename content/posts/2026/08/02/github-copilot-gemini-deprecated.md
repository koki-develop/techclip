---
date: "2026-08-02T14:58:48+09:00"
title: "GitHub Copilot、Gemini 2.5 ProとGemini 3 Flashを廃止 後継モデルへの移行が必須に"
description: "GitHubがCopilotの全機能からGemini 2.5 ProとGemini 3 Flashの提供を2026年7月31日付で終了し、利用者にGemini 3.1 ProやGemini 3.6 Flashへの移行を求めている。"
tags:
  - OSS
  - AI
references:
  - "https://github.blog/changelog/2026-07-31-gemini-2-5-pro-and-gemini-3-flash-deprecated/"
---

## 概要

GitHubは2026年7月31日、GitHub CopilotにおけるGoogleの「Gemini 2.5 Pro」および「Gemini 3 Flash」の提供を終了したと発表した。対象となるのはCopilot Chat、インラインエディット、ask/agentモード、コード補完など、Copilotが提供するほぼ全ての体験にわたる。両モデルはすでに選択できなくなっており、これまで利用していたユーザーは後継モデルへの切り替えが必要となる。

## 移行先モデルと対応内容

廃止された2モデルの後継として、GitHubはGemini 2.5 Proの代替に「Gemini 3.1 Pro (Preview)」を、Gemini 3 Flashの代替に「Gemini 3.6 Flash」を案内している。個人ユーザーはワークフローや連携ツールで指定しているモデル名を新モデルに更新するだけでよいが、Enterpriseプランを利用する組織の管理者は、Copilotのモデルポリシー設定で新モデルへのアクセスを明示的に有効化する作業が必要になる。なお、廃止されたモデル自体を設定から削除するような追加作業は不要とされている。

## 背景と今後の見通し

GitHubは今回の廃止理由について具体的な説明を公式アナウンスでは示しておらず、Google側での急速なGeminiモデル世代交代に合わせた通常のモデルラインナップ更新の一環とみられる。Copilotは複数のAIベンダーのモデルを選択式で提供する形態を取っており、モデルの新旧交代は今後も定期的に発生する見込みだ。ユーザーやエンタープライズ管理者は、利用中のモデルが将来的に廃止される可能性を踏まえ、Copilotのモデル選択方針や自動化ワークフローを継続的に見直しておくことが求められる。
