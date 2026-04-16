---
date: "2026-04-17T02:37:23+09:00"
title: "Visual Studio 2026 v18.5.0リリース — Copilot Agent強化とJSON Schema最新仕様対応"
description: "MicrosoftがVisual Studio 2026 April Update（v18.5.0）をリリースし、CopilotのAgent Skills自動検出、クラウドエージェント連携、C++コード編集ツールのGA化など多数の改善を加えた。"
tags:
  - Programming Languages
references:
  - "https://learn.microsoft.com/en-us/visualstudio/releases/2026/release-notes"
---

## 概要

Microsoftは2026年4月14日、Visual Studio 2026の最新安定版となる**v18.5.0（April Update）**をリリースした。今回のアップデートは、GitHub Copilotのエージェント機能を中心に大幅な強化が行われており、AI支援による開発体験の向上が主眼となっている。加えて、JSON SchemaのDraft 2019-09/2020-12対応やC++コード編集ツールの正式GA化など、IDEとしての基盤機能も着実に進化している。

## GitHub Copilotのエージェント機能強化

今回の目玉機能の一つが**Agent Skills（エージェントスキル）の自動検出**だ。Copilotエージェントが、リポジトリ内の `.github/skills/`、`.claude/skills/`、`.agents/skills/` といったディレクトリや、ユーザーホームディレクトリ以下の個人スキルフォルダを自動的にスキャンし、`SKILL.md` ファイルとして定義された再利用可能な命令セットを自動的に読み込むようになった。これにより、プロジェクト固有の作業ルールやワークフローをCopilotに覚え込ませる仕組みが大幅に整備された。

また、**クラウドエージェント連携**機能も新たに追加された。Chatウィンドウからクラウドエージェントセッションを直接起動でき、エージェントがリポジトリへのIssue作成やPull Requestの生成を非同期で行う間も、開発者は手元の作業を継続できる。さらに、`.github/agents/` ディレクトリ配下に `.agent.md` ファイルを配置することで、コードレビューや特定ドメインに特化した**カスタムエージェント**を定義することも可能になった。

そのほか、CopilotとIntelliSenseの競合問題に対処するため、**IntelliSenseが補完候補の表示で優先**されるようになり、一度に一つの候補のみが表示される仕様となった。また、過去のCopilotチャット履歴をタイトルやメッセージプレビューとともに閲覧できる**新しいChat Historyパネル**も追加された。

## デバッグ・診断とその他の改善

デバッグ機能では、**テキストビジュアライザへのAuto-Decoding機能**が追加された。Copilotが変数の値のエンコード形式（Base64、GZipなど）を自動検出してワンクリックで復号・フォーマット表示できるようになった。また**Debugger Agent**という新たなワークフローも導入され、バグのIssueからソースコードの該当箇所の特定、バグの自動再現、トレースポイントの挿入、修正の検証までを自律的に実行できる。

IDE全体の改善としては、JSONエディタが**JSON Schema Draft 2019-09/2020-12**に対応し、`$defs` や `$anchor` といったモダンな機能が利用可能になった。C++開発においては、クラスの継承階層をたどったり関数呼び出しチェーンを追跡したりする**C++コード編集ツール**がエージェントモードでデフォルト有効（GA）となった。

セキュリティ面では、前バージョン（v18.4.4）で対処された複数のCVE（.NETのDoS・なりすまし脆弱性、SQLiteのメモリ破壊、Node.jsのTLS DoS、Visual StudioからInfo Disclosureなど）が今バージョンにも統合されている。
