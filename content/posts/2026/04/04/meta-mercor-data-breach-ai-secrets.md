---
date: "2026-04-04T10:37:37+09:00"
title: "MetaがMercorとの協業停止——LiteLLMサプライチェーン攻撃でAI訓練機密が流出"
description: "オープンソースライブラリLiteLLMへのサプライチェーン攻撃を起点に、AIデータベンダーのMercorが4TBの機密データを盗まれ、MetaがMercorとの協業を一時停止した。"
tags:
  - AI
  - Security
references:
  - "https://www.wired.com/story/meta-mercor-data-breach-ai-industry-secrets/"
  - "https://techcrunch.com/2026/03/31/mercor-says-it-was-hit-by-cyberattack-tied-to-compromise-of-open-source-litellm-project/"
  - "https://fortune.com/2026/04/02/mercor-ai-startup-security-incident-10-billion/"
  - "https://hackread.com/ai-firm-mercor-breach-hackers-4tb-data/"
  - "https://www.techbuzz.ai/articles/meta-halts-mercor-partnership-after-ai-training-data-breach"
  - "https://cybersecuritynews.com/mercor-ai-data-breach/"
---

## 概要

MetaはAIモデルの訓練データ調達に関わるデータベンダー企業Mercorとの協業を一時停止したとWiredが報じた。きっかけは2026年3月下旬に発生したセキュリティインシデントで、オープンソースのAIプロキシライブラリ「LiteLLM」を介したサプライチェーン攻撃により、Mercorのシステムから4TBにおよぶ機密データが盗み出されたとされる。MercorはOpenAI、Anthropic、MetaなどのAI大手にとって、医師・弁護士・研究者といった専門家によるAI訓練データの収集・標注を担う重要なパートナーだ。2025年10月にはFelicis Venturesが主導するシリーズCで3億5000万ドルを調達し、評価額は100億ドルに達している。

## 攻撃の手口：LiteLLMサプライチェーン汚染

攻撃グループ「TeamPCP」は、異なるAIモデル間の通信を仲介するオープンソースライブラリLiteLLMのメンテナーアカウントを侵害し、悪意のあるコードを仕込んだバージョン（1.82.7および1.82.8）をPyPIリポジトリに公開した。これらの不正バージョンがリポジトリに存在したのはわずか約40分間だったが、LiteLLMは毎日数百万回ダウンロードされるライブラリであり、クラウド環境の約36%に導入されているとされる。CI/CDパイプラインで自動的に最新版を取得していた企業は、知らないうちに悪意のあるコードを実行した可能性がある。Mercorはこの攻撃によって認証情報を窃取され、内部システムへの侵入を許した。

## 流出したデータと関与したグループ

別の脅威アクター「Lapsus$」がMercorのリークサイトへの掲載を通じて4TBのデータ窃取を主張している。流出したとされるデータには、候補者プロフィール・個人識別情報（PII）211GB、ソースコード・APIキー・シークレット939GB、ビデオインタビューや身元証明書類3TBが含まれる。さらに、Slackのコミュニケーション記録、内部チケットシステム、MercorのクライアントであるAI大手が手がけている秘密プロジェクトに関する情報も含まれる可能性があるとされており、その点が今回の侵害を単なる個人情報漏洩にとどまらない産業機密問題に押し上げている。セキュリティ研究者はTeamPCPとLapsus$の関連性を示唆しているが、正式な協力関係は確認されていない。

## 業界への影響と今後の展望

AI企業にとって訓練データの収集・選別・準備の手法は、数年間と数十億ドルの投資が積み重なった最重要機密であり、その情報が流出した場合、競合他社が開発期間を数カ月から数年単位で短縮できるリスクが生じる。Metaが主要AIラボとして初めてMercorとの協業停止を公表したことは、AI訓練データ調達における第三者ベンダーのセキュリティ管理の在り方に業界全体として向き合う必要性を示している。今後は、データ処理業務の内製化推進、外部パートナーへの厳格なセキュリティ要件設定、政府によるAI訓練データのセキュリティ基準と漏洩報告義務の整備加速といった動きが予想される。今回の事件はオープンソースのサプライチェーンが短時間で数千の組織に被害を拡大させうる現実を改めて浮き彫りにした。
