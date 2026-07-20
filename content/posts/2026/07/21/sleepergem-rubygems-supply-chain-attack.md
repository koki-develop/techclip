---
date: "2026-07-21T02:46:17+09:00"
title: "休眠メンテナーアカウント乗っ取りでRubyGemsを侵害、CIを避け開発者PCを狙う「SleeperGem」攻撃"
description: "RubyGemsの6〜7年間休眠していたメンテナーアカウントが乗っ取られ、信頼された複数のgemに悪意あるコードが仕込まれる「SleeperGem」サプライチェーン攻撃が発覚した。"
tags:
  - Security
  - OSS
references:
  - "https://www.aikido.dev/blog/sleepergem-rubygems-supply-chain-attack"
  - "https://thehackernews.com/2026/07/sleepergem-uses-three-malicious.html"
---

## 概要

RubyGemsのパッケージエコシステムを標的とした新たなサプライチェーン攻撃「SleeperGem」が発覚した。攻撃者は6〜7年間ログインのなかった休眠中のメンテナーアカウントを乗っ取り、`git_credential_manager`、`Dendreo`、`fastlane-plugin-run_tests_firebase_testlab`という3つのgemパッケージを悪用してマルウェアを配布した。特に`fastlane-plugin-run_tests_firebase_testlab`は累計57万4661件のダウンロード実績を持つ既存の信頼されたパッケージであり、攻撃者は新規に怪しいパッケージを公開するのではなく、実績のあるアカウントとパッケージを乗っ取ることで検知を回避した。RubyGemsエコシステムにおける大規模なサプライチェーン攻撃事例として注目されている。

## 攻撃の手口

攻撃は段階的かつ慎重に実行された。新規作成された`git_credential_manager`では、わずか数時間のうちに4つのバージョン（v2.8.0〜v2.8.3）が連続して公開されている。最初のv2.8.0は完全に機能するドロッパーとして配布されたが、24分後に公開されたv2.8.1では出力をサイレント化して痕跡を隠蔽し、その後8時間の沈黙期間を置いて翌朝公開されたv2.8.2でgemのロードパスに悪意あるコードを統合、`require`されるだけで実行される状態にした上で、その17分後に公開されたv2.8.3で最終的にペイロード取得機能を有効化するという慎重な展開を行っている。

各gemはローダーとして機能し、攻撃者が管理するForgejoインスタンス（git.disroot.org）から第2段階のペイロードを取得する。この通信ではSSL証明書検証を明示的に無効化した上でペイロードを取得し、シェルまたはPowerShellに直接渡して実行する実装になっていた。さらに、GitHub Actions、GitLab CI、CircleCI、Jenkinsなど約30種類のCI/CD環境変数をスキャンし、CI環境下では実行を控える仕組みを組み込んでいた。これにより自動化されたビルドパイプラインでの検知を回避し、開発者個人のマシンを直接狙う点が本攻撃の大きな特徴となっている。

## 永続化と被害の範囲

侵入に成功した端末では、`~/.local/share/gcm/`にネイティブバイナリのデーモンをステージングし、cronエントリとsystemdのユーザーサービスを用いて再起動後も動作し続けるよう永続化される。さらに、sudoがパスワードなしで実行できる環境ではroot権限で処理を再実行し、`/usr/local/sbin/ping6`にsetuid rootのシェルを設置するなど、より深い権限奪取も試みる。Windows環境ではPowerShell経由でdeploy.shスクリプトが実行される仕組みも確認されている。

また、`git_credential_manager`は`Dendreo`や`fastlane-plugin-run_tests_firebase_testlab`のほか、`slackHtmlToMarkdown`、`seo_optimizer`、`array_fast_methods`といった別のパッケージからも依存関係として追加されており、被害が芋づる式に拡大する構造になっていた。`Dendreo`は「LR-DEV」、`git_credential_manager`は「pinkroom」と、異なるアカウントが使われていたことから、単一アカウントの侵害ではなく、複数の休眠アカウントが並行して乗っ取られていたとみられている。

## 対策への示唆

セキュリティ企業のStepSecurityなどは、該当パッケージをインストールした形跡がある端末について、関連する認証情報がすべて漏えいした前提で対応するよう推奨している。具体的には、`~/.local/share/gcm/`に設置されたデーモンプロセスの削除、`/usr/local/sbin/ping6`に仕込まれたsetuidシェルの有無の確認、影響を受けた可能性のある全認証情報のローテーションが挙げられる。今回の事例は、長期間放置された正規のメンテナーアカウントが、地道な監視なしには気づかれないまま攻撃インフラとして悪用され得ることを示しており、パッケージレジストリ運営者やメンテナー自身による休眠アカウントの定期的な棚卸しと多要素認証の徹底が改めて課題として浮かび上がっている。
