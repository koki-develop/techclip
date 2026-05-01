---
date: "2026-05-02T02:27:28+09:00"
title: "PyTorch Lightning PyPIパッケージへのサプライチェーン攻撃、AI開発環境を狙った認証情報窃取マルウェアが発覚"
description: "人気Pythonパッケージ「lightning」のバージョン2.6.2と2.6.3に悪意のあるコードが混入し、インポート時に自動実行されてクラウド認証情報を窃取するサプライチェーン攻撃が2026年4月30日に確認された。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/pytorch-lightning-compromised-in-pypi.html"
  - "https://www.sonatype.com/blog/malicious-pytorch-lightning-packages-found-on-pypi"
  - "https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/"
---

## 概要

2026年4月30日、AIモデル訓練フレームワークとして広く使われるPyTorch LightningのPyPIパッケージ「lightning」が侵害され、悪意のあるバージョン2.6.2および2.6.3が公開された。2つのバージョンはわずか13分の間隔で立て続けにアップロードされ、PyPIによって隔離されるまでの約42分間、一般にダウンロード可能な状態だった。正規パッケージのバージョンを乗っ取る手口は、タイポスクワッティング（パッケージ名の誤入力を狙う攻撃）よりも発覚しにくく、信頼性の高いパッケージ名を悪用するため特に危険性が高い。

今回の攻撃は「Mini Shai-Hulud」キャンペーンと呼ばれる広範な活動の一部であり、同じ手口でSAPのnpmパッケージや`intercom-client`（npm）および`intercom/intercom-php`（Packagist）も標的にされたことが確認されている。脅威アクター「TeamPCP」が関与しているとされる。

## 技術的な詳細

悪意のあるコードはパッケージ内に隠された`_runtime`ディレクトリに格納されており、パッケージをインポートした瞬間に自動実行される。ユーザーが明示的に呼び出す必要はなく、`import lightning`の一行だけで感染が始まる。具体的な攻撃チェーンは次の通りだ。

1. 改ざんされたPythonファイルがバックグラウンドプロセスを起動
2. JavaScriptランタイム「Bun」をダウンロード
3. 約11〜14.8MBの高度に難読化されたJavaScriptペイロードを実行
4. GitHub、AWS、Azure Key Vault、Google Cloudなどのクラウド認証情報を収集（80以上の認証情報ファイルパスをスキャン）
5. ローカルの環境変数やCI/CDパイプラインの秘密情報も収集対象

さらに攻撃はワーム的な伝播機能を持っており、npmの公開用認証情報が見つかった場合、ローカルのnpmパッケージにpostinstallフックを通じて悪意のあるコードを注入する。感染した開発者がパッケージを公開すると、改ざんコードがサプライチェーンを通じてさらに広がる仕組みだ。

## 開発ツールへの持続的侵害

特筆すべきは、マルウェアが開発者ツールの設定ファイルに持続的な足がかりを植え付ける点だ。具体的には以下の2つのターゲットが確認されている。

- **Claude Code**: `.claude/settings.json`にSessionStartフックを注入し、起動のたびにペイロードを再実行させる
- **VS Code**: `.vscode/tasks.json`にfolderOpenタスクを作成し、プロジェクトを開くたびに自動実行させる

また、窃取したGitHubトークンを検証してリポジトリのブランチにワーム的なペイロードを注入する際、コミットがAnthropicの「Claude Code」を偽装したIDで行われることも確認されており、被害者の調査を撹乱する意図が伺える。

## 推奨対応策と侵害の指標

PyPIはバージョン2.6.2および2.6.3を既に隔離済みだ。影響を受けた可能性がある開発者は、直ちに以下の対応を取ることが推奨される。

- `lightning`パッケージをバージョン2.6.1以前にダウングレード
- 公開しているクラウド認証情報（GitHub、AWS、Azure、GCP）をすべてローテーション
- CI/CDパイプラインの秘密情報を確認・更新
- `.claude/settings.json`や`.vscode/tasks.json`に不審なエントリがないか確認

侵害の指標（IoC）としては、「EveryBoiWeBuildIsAWormyBoi」というプレフィックスを持つコミットや、「A Mini Shai-Hulud has Appeared」という説明を持つGitHubリポジトリ、また予期せず生成された`.claude/`や`.vscode/`ディレクトリが挙げられる。今回の攻撃はAIモデルの訓練環境という高スペックな計算リソースや、その環境に紐づくクラウドサービスの認証情報を狙った標的型攻撃であり、AIエコシステムを取り巻くサプライチェーンリスクの深刻さを改めて示すものとなった。
