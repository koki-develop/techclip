---
date: "2026-08-18T14:07:43+09:00"
title: "GitHubで世界的な大規模障害、Actions・PR・認証など主要機能が3時間超停止"
description: "GitHubは8月17日、Webサイト・APIのエラー率が約2割に達する世界的な大規模障害に見舞われ、Actionsやプルリクエスト、認証機能などが3時間19分にわたり影響を受けた。"
tags:
  - Cloud
  - OSS
references:
  - "https://www.forbes.com/sites/conormurray/2026/08/17/what-we-know-about-github-outage-platform-reports-high-error-rates/"
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-confirms-github-is-down-worldwide/"
  - "https://cybersecuritynews.com/github-outage-worldwide/"
---

## 概要

GitHubは8月17日午前9時40分(米東部時間、日本時間同日22時40分)頃から、世界的な大規模障害に見舞われた。GitHub自身がWebサイト・APIへのリクエストの約2割がエラーとなっていることを報告し、Actions、プルリクエスト、Webhooks、Issues、認証機能(SAML/OIDC)、さらにGitHub Copilotまで幅広いサービスが影響を受けた。障害は3時間19分にわたって続き、開発者のコーディングやCI/CDワークフローに世界規模で支障をきたした。運営元のMicrosoftも障害の発生を確認しており、傘下のCopilotやTeamsでも数百件規模の問題報告が上がった。GitHubは全世界で1億8000万人規模のユーザー(開発者)を抱えるプラットフォームであり、今回の障害はその基盤全体に影響を及ぼした可能性がある。

## 影響範囲とタイムライン

障害発生直後、第三者の障害追跡サービスDownDetectorには一時ピークで約3000件のダウン報告が寄せられた。エラー率はサービスによって差があり、Webサイト・APIへのアクセスでは約20%、リポジトリのアーカイブダウンロードでは約50%に達した。一方、PackagesとCodespacesは障害の影響を受けずに稼働を続けたが、Git操作やPagesも障害発生からやや遅れて一時的に影響を受けた。米東部時間12時36分、GitHubは「問題のあるコンポーネントを特定した」と発表して修正措置を実施し、同12時45分にはダウン報告が数百件規模まで減少するなど、回復の兆しが見え始めた。GitHubは修正措置の実施後も「強い回復の兆候」を示しているとして、完全復旧に向けた対応を続けた。

## 背景と今後の課題

今回の障害でGitHubは具体的な根本原因を公表しておらず、記事執筆時点でも調査が継続中とされている。世界中の開発チームが日常的にコード管理、CI/CD、AIコーディング支援を単一プラットフォームに依存している現状において、GitHubのような中核インフラで発生する大規模障害は、開発生産性やリリース作業に直接的な打撃を与える。Microsoft傘下のCopilotやTeamsにも波及したことは、GitHubの基盤がMicrosoftの他サービスとも密接に連携している実態を改めて浮き彫りにした。今後、GitHubから正式な事後分析(ポストモーテム)が公開されるかが注目される。
