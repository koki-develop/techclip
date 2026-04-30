---
date: "2026-05-01T02:36:08+09:00"
title: "uv 0.11.8リリース、Astralミラーからのself-updateやPython探索パスのカスタマイズに対応"
description: "RustベースのPythonパッケージマネージャー「uv」がv0.11.8をリリースし、Astralミラーからのself-updateサポートやPython探索パスのカスタマイズなど複数の新機能と修正が追加された。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://github.com/astral-sh/uv/releases/tag/0.11.8"
---

## 概要

Astral社が開発するRustベースのPythonパッケージマネージャー「uv」は2026年4月27日、バージョン0.11.8をリリースした。本リリースでは、Astralミラーを介したself-updateサポートや、任意のミラーからPythonをダウンロード可能にする新フラグの追加など、使い勝手を向上させる複数の機能強化が含まれている。また、環境変数による設定オプションの拡充や、細かなバグ修正も行われた。

## 新機能と機能強化

最大の目玉の一つは、`python pin`コマンドへの`--python-downloads-json-url`フラグの追加だ。これにより、デフォルト以外の任意のミラーから特定のPythonバージョンをダウンロードできるようになり、ネットワーク制限のある環境や社内ミラーを利用する場面での柔軟性が高まった。また、`uv self update`がAstralミラーからuvそのものを取得する仕組みに対応し、更新の信頼性と速度が改善されている。

その他の機能強化としては、`pip uninstall -y`構文のサポート追加、`uv self version --short`でバージョン番号のみを表示するオプションの追加、空の`SSL_CERT_DIR`ディレクトリに対する不要な警告の抑制、`exclude-newer-span`が存在する場合に`exclude-newer`の省略を許容するロックファイル処理の改善などがある。相対的な`exclude-newer`/`exclude-newer-package`値に対してはセンチネルタイムスタンプが使用されるようになった。

## 環境変数と設定の拡充

設定面では、新しい環境変数が3つ追加された。`UV_PYTHON_NO_REGISTRY`はWindowsレジストリを通じたPythonの自動検出を無効化し、`UV_NO_PROJECT`はプロジェクトファイルの探索を無効化する。さらに`UV_PYTHON_SEARCH_PATH`を使うことで、Pythonインタープリタの探索パスをカスタマイズできるようになった。これらの環境変数は、CI環境での動作の予測可能性を高めたい場合や、特定のPythonバイナリを確実に指定したいケースで役立つ。

## バグ修正

バグ修正では、uv-buildのソースディストリビューションに`rust-toolchain.toml`が含まれていなかった問題が修正された。uvからgitコマンドを呼び出す際にリポジトリの環境変数を引き継いでしまう問題も解消された。また、詳細ログに事前署名済みアップロードURLが平文で表示される問題が修正され、セキュリティが向上している。その他、PEP 517ビルド要件における推移的なURL依存関係の処理の修正、`dependency-groups`のみを持つ`pyproject.toml`での`uv lock`の動作改善、パッチバージョン指定時のPython自動アップグレードの無効化なども含まれる。なお、uv-buildのパッケージメタデータにPython 3.14のclassifierが追加され、PyTorchドキュメントもバージョン2.11向けに更新された。
