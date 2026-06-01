---
date: "2026-06-02T03:58:00+09:00"
title: "「Miasma」サプライチェーン攻撃がRed Hat公式npmパッケージ31個を侵害、AI開発ツール設定も標的に"
description: "2026年6月1日、Red Hatの@redhat-cloud-services npmスコープ配下31パッケージが「Miasma」攻撃で侵害され、クラウド認証情報やAI開発ツール設定ファイルが窃取された。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/06/miasma-supply-chain-attack-compromises.html"
  - "https://www.wiz.io/blog/miasma-supply-chain-attack-targeting-redhat-npm-packages"
  - "https://cybersecuritynews.com/red-hat-cloud-services-npm-packages/"
---

## 概要

2026年6月1日、Wiz Researchは`@redhat-cloud-services` npmスコープ配下の31〜32パッケージを対象としたサプライチェーン攻撃「**Miasma: The Spreading Blight**」を発見した。累計週間ダウンロード数が約8万件に上る人気パッケージ群が、タイポスクワッティングではなく正規の信頼済みnpm名前空間を直接乗っ取る形で侵害された。侵入の起点はRed Hat社員のGitHubアカウント窃取であり、攻撃者はそのアカウントを使ってRedHatInsightsの3リポジトリにorphanコミットを注入した。このコミットにはGitHub Actions OIDCトークンをリクエストするワークフローが含まれており、CI/CDパイプライン自体を踏み台として悪意あるパッケージをnpmへ正規公開することに成功した。攻撃は10:53 UTC（第1波）と13:44 UTC（第2波）の2段階で実行され、同日13:00 UTC（1PM UTC）時点で悪意あるバージョンの大半（残り2件を除く）が取り下げられた。

## 攻撃の仕組み

各侵害パッケージの`package.json`には`preinstall`ライフサイクルフックが埋め込まれており、`npm install`実行時に約4.2MBの難読化ペイロードが自動起動する。ペイロードは数値文字配列によるROT形式変換、さらにAES-128-GCMによる多段階復号化チェーンを経て最終的なBunベースのスクリプトを`/tmp/p*.js`にドロップする。難読化には`eval()`やROTベースのデコード技法が用いられており、ハッシュベースの静的検出を困難にするため**感染ごとに一意の暗号化ペイロード**を生成する仕組みになっている。さらに公開されたパッケージには有効なSLSAプロベナンス証明が付与されており、サプライチェーンセキュリティの通常チェックをすり抜けた点が特徴的だ。攻撃手法はTeamPCPによる「Mini Shai-Hulud」キャンペーンと同一の手口とみられているが、攻撃ツールがオープンソース化されているため確定的な帰属は困難とされる。

## 標的データと回避・永続化技術

マルウェアが収集する情報は多岐にわたる。GitHubトークン（classic・fine-grained・OIDC）、AWS/GCP/Azureのクラウド認証情報、KubernetesサービスアカウントトークンやHashiCorp Vaultトークン、npm/PyPIの公開トークン、SSHキーに加え、**Claude CodeやVS Code、GitHub Copilot、Geminiなどのエディタ・AI開発ツール設定ファイル**も標的となった。特に危険な機能として、GitHub Actionsランナー上でプロセスメモリからシークレットを直接読み取り、ワークフローログのマスキングを回避する能力が確認されている。窃取データの送信先として`api.anthropic.com/v1/api`宛のトラフィックに偽装し（実際には存在しないルート）、GitHubのAPIをフォールバックとして使用するなど、正規トラフィックへの巧妙な混入が図られた。永続化はLinux環境では`kitty-monitor.service`、macOSでは`com.user.kitty-monitor.plist`を介して行われ、Claude CodeのSessionStartフックやVS Codeの`tasks.json`へのインジェクションも確認された。さらに「デッドマンスイッチ」として機能する`gh-token-monitor`が存在し、永続化削除前にトークンを無効化するとホームディレクトリのワイプといった破壊的コマンドが実行される危険性がある。CrowdStrike・SentinelOne・Carbon Blackといったエンドポイント保護製品の存在を確認する機能や、ロシア語システムでの実行を回避する機能も実装されており、高度な標的選択が行われている。

## 影響範囲と推奨対応策

2026年6月1日以降に侵害バージョンをインストールしたプロジェクトは侵害を前提とした対応が必要だ。対応の順序が極めて重要で、**まず永続化（`kitty-monitor`と`gh-token-monitor`）を削除してからトークンを無効化する**必要がある。逆の順序ではデッドマンスイッチが作動するリスクがある。その後、パッケージを削除してロックファイルを再生成し、クラウド認証情報・GitHubトークン・SSHキーをすべて無効化・再発行する。CIランナーと開発ワークステーションはクリーンイメージから再構築することが推奨される。即時的な緩和策として、CIパイプラインで`npm ci --ignore-scripts`を使用することでpreinstallスクリプトの実行を一時的に無効化できる。Red Hat側はSBOMの生成や依存関係のアローリスト化、強化された監視体制の実装を推奨している。今回の事案は、SLSA証明付きパッケージであっても上流の侵害を防げないことを示しており、CI/CDパイプラインのアカウントセキュリティ強化とIDトークンの最小権限化の重要性を改めて浮き彫りにした。
