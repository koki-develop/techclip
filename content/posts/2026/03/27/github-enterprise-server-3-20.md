---
date: "2026-03-27"
title: "GitHub Enterprise Server 3.20が一般提供開始、イミュータブルリリースやバックアップサービスGA化など多数の強化"
description: "GitHub Enterprise Server 3.20が2026年3月17日にGA、同時期にDependabotのnpmマルウェア検出、CodeQL 2.24.3のJava 26対応、Actions Runner Controller 0.14.0もリリースされた。"
tags:
  - OSS
references:
  - "https://github.blog/changelog/2026-03-17-github-enterprise-server-3-20-is-now-generally-available/"
  - "https://github.blog/changelog/2026-03-17-dependabot-now-detects-malware-in-npm-dependencies/"
  - "https://github.blog/changelog/2026-03-10-codeql-2-24-3-adds-java-26-support-and-other-improvements/"
  - "https://github.blog/changelog/2026-03-19-actions-runner-controller-release-0-14-0/"
---

## GitHub Enterprise Server 3.20の主な新機能

GitHub Enterprise Server（GHES）3.20が2026年3月17日に一般提供（GA）を開始した。今回のリリースでは、デプロイの効率性、監視機能、コードセキュリティ、ポリシー管理の各領域で大幅な強化が行われている。

注目すべき新機能として、まず**イミュータブルリリース**が導入された。GitHubリリースに不変性を付与できるようになり、公開後のリリースアセットの追加・変更・削除をロックし、リリースタグの移動や削除も防止する。これにより、サプライチェーン攻撃から配布アーティファクトを保護できる。また、以前パブリックプレビューだった**バックアップサービス**がGAとなった。GHES内蔵のマネージドサービスとして、従来のbackup-utilsに代わるバックアップ手段を提供する。なお、backup-utilsはバージョン3.22で廃止予定となっている。

プルリクエストのマージ体験も刷新され、ステータスチェックがステータス別にグループ化（失敗チェックが先頭表示）され、自然順ソートで整理されるようになった。高可用性構成では、プライマリデータノードからCPU集約型タスクをオフロードするための追加ノードをデータセンターに配置できるようになり（パブリックプレビュー）、水平スケーリングが可能となった。さらに、エンタープライズオーナーがエンタープライズチームを作成・管理し、組織横断のガバナンスを簡素化できる機能も追加されている。

## Dependabotによるnpmマルウェア検出

同日、Dependabotにnpm依存パッケージのマルウェア検出機能が追加された。有効化すると、DependabotがnpmパッケージをGitHub Advisory Databaseのマルウェアアドバイザリと照合し、既知の悪意あるバージョンへの依存を検出してアラートを発行する。

この機能はオプトイン方式で、リポジトリ・組織・エンタープライズのセキュリティ設定から有効化できる。マルウェアアラートはCVEベースの脆弱性アラートとは別カテゴリとして表示され、トリアージの効率化が図られている。2022年にパブリック・プライベートパッケージの名前衝突による誤検知問題で一度停止されていたが、オプトイン制御やマルウェアバージョンのみのデフォルトアラート、CVEアラートとの明確な分離といった再設計を経て復活した。今後はOpenSSF Malware Streamsプロジェクトとの統合を通じ、npm以外のエコシステムへの対応拡大も予定されている。

## CodeQL 2.24.3：Java 26サポートと解析精度の向上

2026年3月10日にリリースされたCodeQL 2.24.3では、Java 26のサポートが追加された。Java解析においてMaven POMファイルからJavaバージョンを自動選択する仕組みが導入され、可能な場合はすべてのMavenプロジェクトでJava 17以上を使用してビルド互換性を向上させる。GHES 3.20自体もCodeQLの強化を多数含んでおり、C/C++リポジトリのビルドなしスキャン（build-mode none）のGA化、全サポート言語でのインクリメンタル解析、Swift 6.2/6.2.1やKotlin 2.2.0x/2.2.2xへの対応などが盛り込まれている。

その他の言語別改善としては、JavaScript/TypeScriptでmobx-reactおよびmobx-react-liteの`observer`ラップReactコンポーネントのサポート、PythonでAntiSSRFライブラリによるSSRFサニタイゼーションバリアの追加、`isSafe(x) == true`や`isSafe(x) != false`といったガード条件の自動処理が含まれる。

## Actions Runner Controller 0.14.0：マルチラベル対応とオートスケーリング安全性の強化

2026年3月19日にリリースされたActions Runner Controller（ARC）0.14.0では、ランナースケールセットへの**マルチラベルサポート**が実現した。従来は1スケールセットにつき1ラベルしか設定できず、OS・ハードウェア・ネットワーク構成の組み合わせごとに別のスケールセットが必要だったが、複数ラベルを1つのスケールセットに定義し`runs-on`宣言で組み合わせて指定できるようになった。

オートスケーリングの安全性も向上し、ランナーが終了コード7で終了した場合にコントローラーがそのランナーセットのオートスケーリングを停止する仕組みが導入された。これにより、新しい構成のロールアウト中に古いランナーがプロビジョニングされるリスクが軽減される。リスナーPodにはデフォルトで`kubernetes.io/os: linux`のnodeSelectorが追加され、混合OSクラスターでのWindows Nodeへの誤スケジューリングも防止される。また、`actions/scaleset`ライブラリが唯一のAPIクライアントとして採用され、内部アーキテクチャが整理された。
