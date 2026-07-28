---
date: "2026-07-29T02:33:54+09:00"
title: "偽Claude Desktopアプリの広告キャンペーン「FakeAgent」、claude.aiドメインを悪用しSectopRATが29組織に感染"
description: "Bing広告とAnthropicのClaude Artifacts機能を悪用した「FakeAgent」キャンペーンにより、少なくとも29組織が情報窃取型マルウェアSectopRATに感染したことが判明した。"
tags:
  - Security
  - AI
references:
  - "https://www.huntress.com/blog/fakeagent-claude-desktop-malvertising-ends-in-dotnet-rat"
  - "https://www.bleepingcomputer.com/news/security/fake-claude-app-promoted-by-bing-ads-pushes-sectoprat-malware/"
  - "https://www.helpnetsecurity.com/2026/07/23/anthropic-claude-artifacts-download-malware/"
---

## 概要

セキュリティ企業Huntressは、Bing広告とAnthropicのClaude Artifacts機能を悪用したマルバタイジング（悪意ある広告）キャンペーン「FakeAgent」を報告した。攻撃者はBingの検索広告経由でユーザーを正規のclaude.aiドメイン上に公開された悪性のArtifactへ誘導し、そこから偽の「Claude Desktop」インストーラーをダウンロードさせる手口で、2026年7月21日から22日にかけて少なくとも29組織に情報窃取型マルウェア「SectopRAT」を感染させた。該当のArtifactは削除されるまでに7,100回以上閲覧されており、被害範囲の大きさがうかがえる。Anthropicは報告を受けて当該Artifactを削除している。

## 攻撃の手口

ユーザーが「CLAUDE DESKTOP APP」などで検索すると、Bingの検索結果にスポンサーリンクとして悪性のClaude Artifactへのリンクが表示される。このArtifactは正規のインストール手順を装ったページになっており、左上には「Content is user-generated and unverified（コンテンツはユーザー生成であり未検証）」という注意書きが表示されていたものの、目立たず容易に見落とされる状態だった。ダウンロードボタンをクリックすると、`claude.ai.download-app[.]us`のような紛らわしい外部ドメインへリダイレクトされ、`ClaudeDesktop.exe`という名前の実行ファイルが配布される仕組みになっていた。

## マルウェアの技術的詳細

配布された`ClaudeDesktop.exe`は、実際にはJetBrains製の正規署名済みバイナリ`jcef_helper.exe`であり、改ざんされた`libcef.dll`をDLLサイドローディングで読み込ませることで悪性コードを実行する多段構成になっていた。さらに二段目としてIBM SPSSの正規バイナリ`sslconf.exe`が悪性の`tempdir.dll`をサイドロードし、最終的に.NET製のSectopRATペイロードが実行される。感染後は`DockerDesktop.exe`という名前でスケジュールタスクに登録され、永続化と再感染を維持する。マルウェア自体にはVMProtectによる商用パッキング、GPU・VRAM情報を用いた仮想マシン検知、DirectXのシェーダーを用いた独自のAES-256-CTR復号処理など、解析回避のための高度な防御機構が組み込まれていた。C2通信にはイーサリアムのブロックチェーン上にコマンドを隠す「EtherHiding」という手法が用いられており、Huntressの調査では2025年5月から2026年6月にかけて使われた21件のC2アドレスがBSC上のトランザクションから追加で発見されている。SectopRATはクレジットカード情報、ブラウザに保存された認証情報、FTPアカウント、Discordなどのメッセージングアプリのデータ、VPN情報などを窃取する機能に加え、HVNC(Hidden VNC)による遠隔操作機能も備える。

## 攻撃者の特定とAnthropicの対応

Huntressはドメイン登録情報に含まれるメールアドレスを手がかりに攻撃者のインフラを追跡し、同一のメールアドレスで登録された10件のドメインを特定した。関連ドメインの一つ`polse[.]us`は、マイクロソフトの「Operation Endgame」によってすでに押収されていたことも判明している。なお、Huntressの解析チームはシェーダーベースの暗号処理を解読するためのSM5バイトコードエミュレーションなど、今回の技術解析にClaude Opus 4.8を活用したとしており、AIを悪用した攻撃をAIで解析するという構図も注目された。Anthropicは通報を受けて該当のArtifactを削除したが、ユーザー生成コンテンツをホストするAI関連プラットフォームが、正規ドメインの信頼性を逆手に取ったマルウェア配布経路として悪用され得ることを示す事例として、今後同様の対策強化が求められる。
