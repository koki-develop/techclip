---
date: "2026-08-16T08:02:20+09:00"
title: "Google CloudのDatabase Migration ServiceがGemini搭載、ストアドプロシージャ移行の「最後の1マイル」を解消"
description: "Google CloudがDatabase Migration ServiceにGeminiによるAIコード変換機能を追加し、OracleやSQL ServerからPostgreSQLへのストアドプロシージャ移行を数ヶ月から数日に短縮できるようにした。"
tags:
  - Cloud
  - AI
references:
  - "https://cloud.google.com/blog/products/databases/accelerate-postgresql-migrations-with-gemini-in-dms"
---

## 概要

Google Cloudは8月11日、Database Migration Service（DMS）にGeminiを統合したAIコード変換機能を発表した。OracleやSQL ServerからPostgreSQL（AlloyDB for PostgreSQLおよびCloud SQL for PostgreSQL）へのデータベース移行において、これまで数ヶ月を要していたストアドプロシージャ・トリガー・カスタム関数などの手続き型ロジックの変換作業を、数日単位に短縮できるとしている。

## 「最後の1マイル」問題

Google Cloudによれば、データベース移行はスキーマ変換やデータ移行そのものは比較的スムーズに進む一方、数百個に及ぶストアドプロシージャやトリガー、カスタム関数を専有のSQL方言（PL/SQLやT-SQLなど）からPostgreSQLのPL/pgSQLへ手作業で書き換える工程がボトルネックとなってきた。数千行規模の手続き型コードを人手で翻訳するには長い期間がかかるうえ、変換ミスによるリスクも高い。この「最後の1マイル」を解消することが、今回の機能追加の主眼だという。

## 技術的な詳細

新機能は、ソースデータベースのテーブル関係やデータ型、外部キー制約、プロシージャ間の依存関係といったスキーマ全体のコンテキストを自動的に読み込んだ上で、Geminiが変換対象のコードを生成する仕組みを採る。標準的なDDLやスカラ関数の変換には決定論的なコンパイラルールによる1対1マッピングを用い、条件分岐やNULLハンドリングなど複雑な手続きブロックの変換にGeminiのコンテキスト理解を組み合わせることで精度を担保する。生成後は構文・依存関係の自動検証を経て、変換前後のコードをサイドバイサイドで表示し、変換理由をインラインで説明する評価画面が提示される。開発者はここで内容を確認・編集した上で、Cloud SQLやAlloyDB上のステージング環境にデプロイして機能・性能を検証できる。処理はすべて利用組織のGoogle CloudプロジェクトIAMガバナンス配下で完結するため、複数ファイルの手作業コピー&ペーストや、コードの外部持ち出しを避けられる点もセキュリティ面での特徴として挙げられている。

## 利用方法と今後

機能はGoogle Cloudコンソールのmigration assessmentウィザードから呼び出す形で提供される。記事では料金体系やプレビュー・GA(一般提供)の区分については明記されておらず、詳細はデータベース移行および料金の公式ドキュメントを参照する必要がある。あわせて公開された動画シリーズ「Gemini taught me PostgreSQL」では、OracleやSQL Serverからの典型的な変換シナリオが紹介されている。Google Cloudは関連するデータベース運用エージェントや、複数結果セットの変換自動化といった取り組みも進めており、AIを活用したデータベース移行・運用の自動化を今後も拡張していく方針とみられる。
