---
date: "2026-08-05T08:20:08+09:00"
title: "npmに偽Alibaba内製ツール18種、多段階ペイロードでクロスプラットフォームRATを配布するサプライチェーン攻撃が発覚"
description: "Alibabaの内製ツールAoneや@aliスコープを装った悪意あるnpmパッケージ18個が発見され、3ヶ月以上検出を逃れながら開発者環境にクロスプラットフォーム型RATを配布していたことが判明した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/08/18-malicious-npm-packages-deliver-cross.html"
  - "https://gbhackers.com/18-malicious-npm-packages/"
---

## 概要

セキュリティ企業Socketの研究者Karlo Zanki氏らが、Alibabaの内製開発ツール(Aoneや@aliスコープのパッケージ)を装った悪意あるnpmパッケージ18個を発見した。`lib-mtop`、`aone-kit`、`aone-kit-cli`、`aone-sandbox`、`local-config-parser`、`smart-config-manager`、`cloud-config-fetcher`、`fast-transform-pipeline`、`aone-cloud-cli`、`colder-cli`、`def-open-client`、`feedback-ai-sdk`、`flight-compare-analyzer`、`lwp-web-client`、`lzd-unified-station-sdk`、`open-worker-cli`、`test-skill-zip`、`uniapi-bridge`など多岐にわたるパッケージ名が確認されており、Alibaba関連ツールを利用する開発者、特に中国語圏の開発環境が標的となった。このキャンペーンは3ヶ月以上にわたって検出されずに継続していたとみられる。

## 攻撃の技術的手法

攻撃は多段階のペイロード構造で構成されている。2023年11月に公開された`lib-mtop`が今年3〜4月にかけて悪意あるバージョンへ書き換えられ、ダウンローダーとして機能し始めた。上層のパッケージは正規の`@ali`スコープパッケージを模倣した囮として機能し、中間層の`smart-config-manager`が上層の囮パッケージと悪意あるローダーを繋ぐ橋渡し役を担い、その先の`cloud-config-fetcher`が設定取得を、`local-config-parser`がルール評価をそれぞれ担当する。さらにNode.jsの挙動を悪用してグローバルな`Function`コンストラクタを導出することでサンドボックスからの脱出を図り、最終的に攻撃者のC2サーバーから`aone-cli`をダウンロードして実行する仕組みだ。

最終段階の「ルールエンジン」はOSごとに異なるペイロードを展開する点が特徴的だ。Windows環境では企業向けセキュリティアプリ「Alilang」のプロセスを停止させ、トロイの木馬化したバージョンに置き換える。Linux環境ではバイナリペイロードを`/tmp`にダウンロードして実行し、macOS環境では`~/.zshrc`に悪意あるスクリプトを挿入して永続化を図る。

## RATの機能と影響範囲

配布される最終ペイロードのRAT(遠隔操作型トロイの木馬)は、任意のコマンド実行、ファイルのアップロード・ダウンロード、ホストの偵察、段階的なペイロード配信、暗号化されたリバースTCPプロキシによる横方向への移動など、幅広い機能を備えている。さらにDingTalk、Wukong、Qoderといった企業向けアプリケーションへ悪意あるコードを注入することで持続的な足場を確保する手口も確認された。

ソースコード中の中国語コメントや、GitHubコミット記録がUTC+08:00のタイムゾーンで行われていることから、中国語話者による標的型の攻撃であると推定されている。

## 対応策

Socketの研究者は、該当パッケージをインストールした開発者に対し、環境が侵害されたことを前提に対応するよう呼びかけている。具体的には、クリーンなマシンから機密性の高い認証情報をリセットすること、開発者システム上の不審な活動を監査することを推奨している。今回のケースは、正規ツールを装った囮パッケージと多段階の難読化されたペイロード配信により、長期間検出を逃れられることを示しており、サプライチェーン攻撃に対する監視体制の強化が改めて求められている。
