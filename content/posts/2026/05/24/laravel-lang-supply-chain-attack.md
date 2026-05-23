---
date: "2026-05-24T02:26:57+09:00"
title: "Laravel-Langパッケージがサプライチェーン攻撃で侵害、700以上のバージョンに認証情報窃取マルウェア"
description: "LaravelのローカライゼーションライブラリLaravel-Langの233バージョンがサプライチェーン攻撃で侵害され、AWS・GCP・Azure等のクラウド認証情報を窃取するマルウェアが仕込まれた。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/05/laravel-lang-php-packages-compromised.html"
  - "https://cybersecuritynews.com/laravel-lang-packages-compromised/"
  - "https://socket.dev/blog/laravel-lang-compromise"
---

## 概要

2026年5月22〜23日、Laravelアプリケーションのローカライゼーションライブラリとして広く使われているLaravel-Langの複数パッケージがサプライチェーン攻撃を受けた。SocketとAikidoのセキュリティ研究者が発見したこの侵害では、`laravel-lang/lang`・`laravel-lang/http-statuses`・`laravel-lang/attributes`・`laravel-lang/actions`の4パッケージ合計233バージョン以上が悪意あるコードを含む形で公開され、700以上のGitHubリポジトリが関与していた。なお、これらはPHPフレームワーク本体（Laravel公式）ではなく、コミュニティが保守する多言語化パッケージである。

攻撃の痕跡として、複数のリポジトリで秒単位の間隔で大量のバージョンタグが発行されており、自動化されたスクリプトによる組織レベルの認証情報侵害が強く疑われている。

## 攻撃手法：Composerオートローダーを悪用した自動実行

攻撃者はGitHubのバージョンタグシステムを悪用し、正規のタグを悪意あるフォークのコミットに向け直す手口を用いた。開発者がComposer経由でパッケージを取得すると、パッケージ内の`src/helpers.php`がComposerのオートロード設定に登録されており、**Laravelアプリケーションの起動時に自動実行**される仕組みになっていた。クラスのインスタンス化や特定の関数呼び出しは不要で、`vendor/autoload.php`を読み込むだけでペイロードが走る。

初期ドロッパーは難読化された文字コード配列を用いてC2サーバー（`flipboxstudio[.]info`）と通信し、二次ペイロードをダウンロードする。TLS証明書の検証は無効化されており、一時ディレクトリ（`sys_get_temp_dir()/.laravel_locale/`）を作業領域として使用する。

## マルウェアの窃取能力

ダウンロードされる二次ペイロードは約5,900行のPHP製スティーラーで、15〜17個の専門的な収集モジュールで構成されている。窃取対象は広範にわたる。

**クラウド・インフラ系**ではAWS IAMロールやメタデータエンドポイント（169.254.169.254）・GCP・Azure・DigitalOcean・Herokuの認証情報、KubernetesサービスアカウントトークンおよびHashiCorp Vault設定が対象となる。**CI/CDパイプライン**ではJenkins・GitLab Runner・GitHub Actions・CircleCI・TravisCI・ArgoCDの設定・シークレットが盗まれる。**開発ツール**ではSSH秘密鍵・Git認証情報・Dockerトークン・`.env`ファイルが対象だ。これに加え、Chrome・Firefox・Edge等のブラウザパスワード、1Password・Bitwarden・LastPassなどのパスワードマネージャーデータ、MetaMaskやElectrumなどの暗号資産ウォレット、VPN設定、Discord・Slack・Telegramのセッショントークンも収集される。

収集したデータはAES-256で暗号化したうえで`flipboxstudio[.]info/exfil`に送信され、その後スティーラー自身を削除してフォレンジック証拠を消去する。

## 推奨される対応

影響を受けたパッケージを使用している場合、侵害が疑われるシステムは**完全に危険な状態として扱い**、既知の正常なイメージから環境を再構築することが推奨されている。加えて以下の順でシークレットをローテーションする必要がある。

1. クラウド認証情報（AWS・GCP・Azure）
2. Kubernetes / HashiCorp Vault トークン
3. CI/CDシークレット（GitHub Actions・GitLab・CircleCI等）
4. SSH鍵・Dockerトークン
5. データベース認証情報・その他の`.env`変数

侵害の確認には`composer.lock`で対象パッケージの該当バージョンが含まれていないかチェックし、ネットワークログで`flipboxstudio[.]info`への通信履歴を確認する。一時ファイル`sys_get_temp_dir()/.laravel_locale/`やWindows環境では`DebugChromium.exe`の存在も侵害指標となる。

## まとめと教訓

このインシデントはComposerのオートロード機構という「信頼された実行経路」がサプライチェーン攻撃のベクターになりうることを示している。秒単位での大量タグ発行という異常なリリースパターンを検出できるCI/CDパイプラインの整備や、パッケージのハッシュ検証、最小権限の原則に基づくシークレット管理の重要性が改めて浮き彫りになった。
