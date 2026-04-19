---
date: "2026-04-20T02:17:42+09:00"
title: "MicrosoftがFoundry Localを正式リリース——クラウド不要のAI環境をアプリにバンドルして配布可能に"
description: "MicrosoftがローカルAI実行環境「Foundry Local」を正式リリースし、Windows・Mac・Linux対応のクロスプラットフォームでAIモデルをインストーラ同梱の形で配布できるようになった。"
tags:
  - AI
  - OSS
references:
  - "https://www.publickey1.jp/blog/26/aifoundry_localmaclinux.html"
---

## 概要

Microsoftは2026年4月13日、ローカルAI実行環境「Foundry Local」の正式リリースを発表した。最大の特徴は、AI環境をアプリケーションにバンドルしてインストーラとして配布できる点にある。エンドユーザーが別途クラウドサービスへの接続やモデルのセットアップを行う必要なく、インストールと同時にAI機能をオフライン環境でそのまま利用できる。これにより、クラウドへの依存やネットワーク遅延の問題なく、AIをアプリケーションに深く組み込んだ製品の開発・配布が可能になる。

## 技術的な詳細

ランタイムレイヤーにはONNX RuntimeとWindows MLを採用しており、実行環境のGPU・NPU・CPUを自動的に検出して最適な推論処理を行う。macOSではMetal APIを介してAppleシリコンのGPUにも対応しており、WindowsのみならずMacやLinuxでも同等の機能を利用できるクロスプラットフォーム対応となっている。

APIは、OpenAIのRESTful APIと互換性のある「Foundry Local Core API」として提供される。そのため、既存のOpenAI API対応コードからの移行が容易で、JavaScript・C#・Python・Rustの各言語向けSDKが用意されている。利用可能なモデルはGPT OSS、Qwen Family、Deepseek、Whisper、Mistral、Phiなど複数ファミリーから選択でき、用途や実行環境に応じたモデルサイズの使い分けも可能だ。

## 今後の展望

Microsoftは今後、AIモデルカタログの拡充、NPU・GPU対応デバイスのさらなる拡大、リアルタイム文字起こし機能の追加、そして複数アプリケーション間でのモデル共有機能といった強化を予定している。エッジ・オフライン環境でのAI活用ニーズが高まる中、配布可能な形でのローカルAIインフラを整備する同社の取り組みは、エンタープライズ向けアプリ開発においても注目される。
