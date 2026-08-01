---
date: "2026-08-01T20:25:53+09:00"
title: "Vercel Labs、Node.js不要でTypeScriptをネイティブバイナリ化する「scriptc」を公開"
description: "Vercel Labsが、TypeScriptをNode.jsやJSエンジンなしでLLVM経由のネイティブバイナリに直接コンパイルするオープンソースコンパイラ「scriptc」を公開した。"
tags:
  - Programming Languages
  - OSS
references:
  - "https://github.com/vercel-labs/scriptc"
---

## 概要

Vercel Labsは7月26日、TypeScriptをNode.jsやV8などのJavaScriptエンジンを一切バンドルせずにネイティブバイナリへ直接コンパイルするオープンソースコンパイラ「scriptc」を公開した。コンセプトは「Zero-runtime TypeScript」で、生成されるバイナリはわずか170〜200KB程度に収まる。Hacker Newsでも取り上げられ、注目を集めている。

scriptcは対応可能なコードを静的にネイティブコードへコンパイルすることを基本とし、それが不可能な構文については組み込みのJavaScriptエンジン（quickjs-ng、約620KB）で動的に実行する`--dynamic`フラグを用意している。逆にコンパイル不可能な構文には明示的なエラーコードを返して報告する仕組みで、静的コンパイルの適用範囲を`scriptc coverage`コマンドで事前に分析できる点も特徴だ。

## 技術的な詳細

言語機能としては、クラスと単一継承、動的ディスパッチ、クロージャ、ジェネリクス（単形化）、判別可能な共用体、async/await、例外処理といった標準的なTypeScriptの機能をサポートする。標準ライブラリはUTF-16完全互換の文字列やJSと同じ順序を保つArray/Map/Set、JSON、Math、型付き配列、Bufferなどを備え、ファイルシステムやパス操作、子プロセス、暗号化、圧縮、タイマーといったNode.js APIとの互換性も持たせている。さらにnet、http、https、tls、dgram、dnsなどのサーバースタックやfetch APIにも対応し、TLSはmbedTLSを内蔵する。

コード生成基盤にはLLVMをデフォルトで採用している。特筆すべき機能として、TypeScriptコードをビルド時に隔離されたVM内で実行し、その結果をリテラルとしてバイナリに埋め込む「comptime」や、C ABIを直接呼び出す「ネイティブFFI」（`--ffi`フラグ）がある。FFIでは署名のみのTypeScript宣言をC ABI呼び出しにバインドし、マニフェストで宣言したアーカイブやオブジェクト、システムライブラリをリンクできる。また`JSON.parse(...) as Config`のような型アサーションには実行時検証を挿入し、型不一致時に詳細なエラーを投げるオプションも用意されている。

パフォーマンス面では、Apple M系チップでの計測で起動時間が約2.4ミリ秒（Node.jsの約47ミリ秒に対して大幅に高速）、メモリ使用量は1〜4MB程度（RSS、Node.jsの67〜116MBと比較）とされている。バイナリサイズも静的コンパイル時で170〜200KB、動的実行を含めても約3MBとGo言語のバイナリ（約2MB）と比較しても遜色ない水準に収まる。

正確性の検証には、800件以上のコーパスを用いてNode.jsとネイティブ実行の出力を突き合わせる差分テストと、AddressSanitizerによるメモリ安全性検証の両方を用いている。プロジェクトは`packages/compiler`（tsc APIを用いたフロントエンドとLLVM/Cバックエンド）、`packages/runtime`（参照カウントとサイクルコレクタ、スタックフルファイバ、イベントループを備えたCランタイム）、`packages/cli`の3パッケージで構成される。

## 制限事項と今後の展望

現時点ではmacOS arm64を主要プラットフォームとし、LinuxとWindowsはクロスコンパイルでビルドしつつ専用のテストレーンで検証している。npmの依存パッケージは`--dynamic`フラグ使用時のみ利用可能で、オプションパラメータを値として扱う関数や一部の非同期処理（Promise.rejectなど）は現状コンパイルできない制限がある。開発チームはロードマップとして整数型推論や所有権分析の追加を計画しているという。ライセンスはApache License 2.0で公開されている。
