---
date: "2026-04-03T18:17:14+09:00"
title: "VS Code Python拡張機能 2026年3月版：Rustベース並列インデクサーで平均10倍高速化、venvシンボル検索も追加"
description: "MicrosoftがVS Code向けPython拡張機能の2026年3月版をリリースし、Rustベースの並列インデクサーによる大幅なパフォーマンス向上とPylanceのvenv内シンボル検索機能を導入した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://devblogs.microsoft.com/python/python-in-visual-studio-code-march-2026-release/"
---

## 概要

MicrosoftはVS Code向けPython拡張機能の2026年3月版を4月1日にリリースした。今回のリリースでは、コード探索の効率を高める新機能と、実験的なパフォーマンス改善が主なハイライトとなっている。開発者の日常的なワークフローを加速する2つの大きな機能追加に加え、Python Environments拡張機能のいくつかの改善も含まれている。

## インストール済みパッケージのシンボル検索

Pylanceがアクティブな仮想環境（venv）内のパッケージシンボルをワークスペース検索（`Cmd/Ctrl+T`）に含められるようになった。これにより、サードパーティライブラリの関数やクラスをVS Codeを離れることなく素早く探し出せるようになる。

この機能は設定「**Python › Analysis: Include Venv In Workspace Symbols**」で制御される。デフォルトではオフになっており、パフォーマンスへの影響を考慮してオプトイン方式を採用している。`py.typed`を持たないライブラリの場合、`__init__.py`や`__all__`でエクスポートされたシンボルのみがインデックスされる。インデックスの深さはパッケージごとに「**Python › Analysis: Package Index Depths**」設定で細かく調整することも可能だ。

## 実験的機能：Rustベース並列インデクサー

今回のリリースで最も注目される機能が、実験的なRustベースの並列インデクサーだ。設定「**Python › Analysis: Enable Parallel Indexing**」を有効にすると、Pylanceのインデクサーがアウトプロセスで動作するRust実装に切り替わる。大規模なPythonプロジェクトでは平均10倍のパフォーマンス向上が期待でき、ワークスペースを開いた直後の補完応答速度やIntelliSenseの反応性が大幅に改善される。プロジェクト規模が大きいほど効果が顕著に現れるため、大型コードベースを扱う開発者には特に有効だ。現在は意図的に実験的ステータスとしてリリースされており、MicrosoftはPylanceのGitHubリポジトリを通じてユーザーフィードバックを募集している。

## Python Environments拡張機能の改善

Python Environments拡張機能にもいくつかの改善が加えられた。ワークスペースのインタープリター選択がターミナルでアクティブ化された環境よりも優先されるようになり、より一貫した動作が期待できる。また、環境ファイルの変更通知に「今後表示しない」オプションが追加され、通知の煩わしさを低減できるようになった。さらに、Pixi環境が検出された場合にPixi拡張機能が推奨されるようになった。

これらの機能はVS Codeの拡張機能マーケットプレイス（`Ctrl+Shift+X`）から最新版に更新することで利用できる。
