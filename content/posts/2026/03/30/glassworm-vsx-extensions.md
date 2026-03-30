---
date: "2026-03-30"
title: "サプライチェーン攻撃「GlassWorm」が開発者を標的に、433件超のリポジトリ・拡張機能を悪用しSolanaでC2通信"
description: "GlassWormと呼ばれるサプライチェーン攻撃キャンペーンがOpen VSX拡張機能72件やGitHub・npmなど400以上のリポジトリを悪用し、Solanaブロックチェーンを介したC2通信で開発者の認証情報や暗号資産を窃取していることが判明した。"
tags:
  - Security
  - OSS
references:
  - "https://thehackernews.com/2026/03/glassworm-supply-chain-attack-abuses-72.html"
  - "https://www.bleepingcomputer.com/news/security/glassworm-malware-hits-400-plus-code-repos-on-github-npm-vscode-openvsx/"
---

## 攻撃の概要と規模

GlassWormは、開発者のソフトウェアサプライチェーンを標的とした大規模な攻撃キャンペーンである。Socket、Aikido Security、Step Security、OpenSourceMalwareコミュニティなど複数のセキュリティ研究機関が調査を進めており、合計433件以上の侵害されたコンポーネントが確認された。内訳はOpen VSX拡張機能72件以上、GitHubリポジトリ351件（Pythonリポジトリ200件、JavaScript/TypeScriptリポジトリ151件）、npmパッケージ10件以上に及ぶ。キャンペーンの痕跡は2025年10月にKoi Securityが最初に検出しており、その後2025年11月から2026年3月にかけて複数の攻撃波が確認されている。

## Solanaブロックチェーンを利用した巧妙なC2メカニズム

GlassWormの最大の特徴は、Solanaブロックチェーンをコマンド＆コントロール（C2）インフラとして利用する斬新な手法にある。マルウェアは5秒ごとにブロックチェーンのトランザクションを照会し、トランザクションメモに埋め込まれたペイロードURLから指令を取得する「デッドドロップリゾルバ」方式を採用している。2025年11月から2026年3月の間に約50件のブロックチェーントランザクションでペイロードURLが更新されており、分散型インフラを活用することで従来のドメインベースのテイクダウンを困難にしている。また、Solanaウォレットをローテーションさせることで追跡回避を図っている。

## 感染手法と難読化技術

攻撃者はVSCode/Open VSXの拡張機能において`extensionPack`や`extensionDependencies`フィールドを悪用し、一見無害なパッケージが信頼を獲得した後に悪意ある別の拡張機能を取り込む「推移的配信」アプローチを採用している。リンター、フォーマッター、AIツールなどを装った拡張機能が確認されており、`angular-studio.ng-angular-extension`や`gvotcha.claude-code-extension`などの具体名が報告されている。GitHubではアカウントを乗っ取って悪意あるコミットをforce-pushする手法が使われ、コミット履歴をLLMで生成したと見られる自然なカバーコミットで偽装する巧妙さも指摘されている。さらに、コードエディタやターミナルでは不可視のUnicode文字を使ってペイロードを隠蔽する難読化技術や、バージョン更新なしにコードを動的に変更できるRemote Dynamic Dependencies（RDD）と呼ばれる手法も用いられている。

## 窃取される情報と検出方法

マルウェアは開発者環境から認証情報・APIトークン・SSH鍵、環境変数・CI/CD認証情報、暗号資産ウォレットの内容、システムメタデータなど広範なデータを窃取する。コード分析からロシア語話者による攻撃が示唆されており、ロシア語ロケールのシステムでは実行をスキップする挙動が確認されているが、決定的な帰属証拠とは言えないと研究者は指摘している。Step Securityは検出指標として、コードベース内のマーカー変数`lzcdrtfxyqiplpd`、ホームディレクトリの`~/init.json`永続化ファイル、予期しないNode.jsインストール、クローンプロジェクト内の不審な`i.js`ファイル、Gitコミット履歴の異常などを確認するよう推奨している。Open VSXは確認された悪意ある拡張機能を削除済みで、開発者には使用中の拡張機能やnpmパッケージの再確認が求められている。
