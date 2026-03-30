---
date: "2026-03-30"
title: "LiteLLMにサプライチェーン攻撃、Trivy CI/CDの侵害を経由しPyPIパッケージにバックドア埋め込み"
description: "攻撃グループTeamPCPがTrivy経由でLiteLLMのCI/CDパイプラインを侵害し、PyPIパッケージv1.82.7・v1.82.8にSSHキーやクラウド認証情報を窃取するマルウェアを仕込んだ。"
tags:
  - Security
  - AI
references:
  - "https://thehackernews.com/2026/03/teampcp-backdoors-litellm-versions.html"
  - "https://docs.litellm.ai/blog/security-update-march-2026"
  - "https://www.helpnetsecurity.com/2026/03/25/teampcp-supply-chain-attacks/"
---

## 事件の概要

2026年3月24日、攻撃グループ「TeamPCP」がAIエージェント向けLLMプロキシライブラリ「LiteLLM」のPyPIパッケージにバックドアを埋め込む攻撃が発覚した。LiteLLMは複数の大規模言語モデルを統一的なインターフェースで切り替えられるライブラリで、月間約9,500万ダウンロードを誇る人気パッケージだ。攻撃者はLiteLLMのCI/CDパイプラインで使用されていたセキュリティスキャナー「Trivy」の侵害を足がかりにして、悪意あるバージョン1.82.7および1.82.8をPyPIに公開した。悪意あるパッケージは10:39 UTCから16:00 UTC（約5時間20分）の間にPyPI上で公開されており、バージョンを固定せずにインストールしたユーザーが影響を受けた可能性がある。FutureSearchの研究者Callum McMahon氏が自身のマシンでペイロードを実行してしまったことで異常に気づき、コミュニティに警告を発したのが発見のきっかけとなった。

## 攻撃の技術的詳細

攻撃は3段階の巧妙な構成で行われた。バージョン1.82.7では`litellm/proxy/proxy_server.py`に悪意あるコードが埋め込まれ、モジュールのインポート時に実行される仕組みだった。さらに攻撃をエスカレートさせたバージョン1.82.8では、`litellm_init.pth`ファイルがパッケージのルートに追加され、LiteLLMをインポートしなくてもPython起動時に自動的にマルウェアが実行されるようになっていた。

マルウェアのペイロードは以下の3つのコンポーネントで構成されていた。第1に、SSHキー、クラウドプロバイダー（AWS、GCP、Azure）の認証情報、Kubernetesシークレット、暗号通貨ウォレット、`.env`ファイルなどを標的とする認証情報ハーベスター。第2に、クラスタノードに特権PodをデプロイするKubernetes横展開ツールキット。第3に、50分ごとに`checkmarx[.]zone/raw`からコマンドを取得する永続的なsystemdバックドア（`sysmon.service`）だ。窃取されたデータは暗号化・圧縮されて`tpcp.tar.gz`にまとめられ、`models.litellm[.]cloud`（LiteLLMとは無関係の不正ドメイン）へHTTPS POSTで送信されていた。

## TeamPCPの広範な攻撃キャンペーン

今回の攻撃は孤立した事件ではなく、TeamPCPによる大規模なサプライチェーン攻撃キャンペーンの一環だ。時系列を追うと、3月1日に最初のサプライチェーン攻撃が公表され、3月19日にAqua SecurityのTrivyセキュリティスキャナーが侵害、3月23日にはCheckMarxのVS Code拡張機能やGitHub Actionsが侵害された。TeamPCPはGitHub Actions、Docker Hub、npm、Open VSX、PyPIの5つのエコシステムにまたがって攻撃を展開しており、侵害した各環境の認証情報を次の標的への踏み台にするという連鎖的な手法を用いている。npmパッケージにPythonバックドアや自己伝播型ワームを埋め込んだ事例や、イランに位置するターゲットに対してKubernetesノードやローカルマシンのワイパーマルウェアを展開した事例も報告されている。

## 対応と推奨される対策

LiteLLMチームは悪意あるパッケージをPyPIから削除し、認証情報のローテーションを実施するとともに、Google Mandiantにフォレンジック調査を依頼した。v1.78.0からv1.82.6までの全リリースについてGitコミットとの整合性を検証し、これらのバージョンの安全性が確認されている。なお、公式のDockerプロキシイメージは依存関係がバージョン固定されていたため影響を受けなかった。

影響を受けた可能性のあるユーザーに対しては、すべてのシークレット（APIキー、データベースパスワード、SSHキー、トークン）のローテーション、`site-packages`内の`litellm_init.pth`の有無の確認と削除、Kubernetesクラスタにおける不正なPodの確認、`models.litellm[.]cloud`や`checkmarx[.]zone`への通信ログの調査、CI/CDパイプラインでのTrivy/KICS使用の監査、そしてLiteLLMをv1.82.6以前にピン留めすることが推奨されている。LLMライブラリはAPIキーや環境変数など機密性の高い設定データにアクセスすることが多いため、今回の攻撃はAI/MLサプライチェーンの脆弱性を浮き彫りにしたといえる。
