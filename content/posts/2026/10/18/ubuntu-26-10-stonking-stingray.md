---
date: "2026-10-18T18:12:04+09:00"
title: "Ubuntu 26.10「Stonking Stingray」リリース、coreutilsのRust移行が完了"
description: "Ubuntu 26.10「Stonking Stingray」が正式リリースされ、coreutilsの全面Rust化やポスト量子署名、ローカル音声認識「Myna」など多数の新機能が追加された。"
tags:
  - OSS
references:
  - "https://linuxiac.com/ubuntu-26-10-released-with-gnome-51-linux-kernel-7-3-and-rust-coreutils/"
  - "https://canonical.com/blog/canonical-releases-ubuntu-26-10-stonking-stingray"
  - "https://www.gamingonlinux.com/2026/10/ubuntu-26-10-stonking-stingray-released/"
---

## 概要

Canonicalは10月15日、Ubuntu 26.10「Stonking Stingray」を正式リリースした。GNOME 51デスクトップとLinuxカーネル7.3を搭載する非LTS版で、サポート期間は2027年7月までの9か月間。次期バージョンのUbuntu 27.04は2027年4月に登場する予定で、安定性を重視するユーザーにはLTS版のUbuntu 26.04が引き続き推奨される。今回の最大の目玉は、GNU coreutilsからRust実装の`uutils`への移行が完了したことで、`cp`、`mv`、`rm`など残っていたコマンド群もRust版に置き換えられ、基盤システムのメモリ安全性が大きく向上した。Ubuntuのエンジニアリング担当VPであるJon Seagerは「Ubuntu 26.10はRustベースのcoreutilsへの移行を完了し、TPMベースのフルディスク暗号化のデバイス対応も拡大した」とコメントしている。

## セキュリティとエンタープライズ機能の強化

セキュリティ面では、OpenSSL 4の採用によりEncrypted Client Hello(ECH)やQUIC機能の拡張、ポスト量子暗号への対応が進んだ。パッケージ署名はGnuPGからRust実装のSequoia PGPに置き換えられ、ポスト量子対応の署名方式へ移行している。さらにopenCryptokiを通じてML-DSAやML-KEMといった量子耐性トークンにも対応した。TPMを活用したフルディスク暗号化は、Hardware Root of Trustを持たないハードウェアにも対応範囲が拡大し、Secure Bootの保護強化も図られている。エンタープライズ向けには、authdサービスを介したMicrosoft Entra ID統合が深化し、パスワード・多要素認証に加えパスキーによるパスワードレスログインが可能になった。システム基盤では、D-Busの実装が従来の`dbus-daemon`から`dbus-broker`に置き換わり信頼性とリソース管理が改善、systemdはバージョン261となり古いSystem Vサービススクリプトのサポートが廃止された。

## デスクトップ体験とAI機能

GNOME 51では、フレームスケジューリングの改善によりアニメーションがより滑らかになり、複数モニター環境の取り扱いも強化された。モニターの輝度設定が再起動後も保持されるようになり(HDR対応含む)、加速度センサー搭載デバイスでの自動画面回転、外部マウス接続時のタッチパッド無効化オプションなどが追加された。FilesアプリやCalendarアプリも応答性が向上し、Papers文書ビューアはPDFの視覚的署名に対応した。Remote Desktopはスマートカードおよびケルベロス認証をサポートする。App CenterはSnapとDEBパッケージの詳細表示を統一し、バージョン・権限・公開者情報・スクリーンショット・パッケージサイズなどを一括確認できるほか、NVIDIAドライバのバージョン選択も専用セクションから行えるようになった。AI関連では、オンデバイスで音声をテキスト化するエージェント「Myna」がオプトイン機能として初登場した。クラウドに音声データを送信せずローカルモデルで処理する仕組みで、デスクトップとの自然な対話操作を目指すものであり、Ubuntu 28.04 LTSではデフォルト機能となる予定だ。

## ハードウェア対応と開発者向け更新

Linuxカーネル7.3(初期パッケージは7.3-rc6ベース)では、Snapdragon X EliteおよびX2 Elite、Intel Xe3P、AMD Zen 6、NVIDIA 615向けのサポートが強化され、Lustreファイルシステムにも対応した。グラフィックス面ではMesa 26.2がGPUサポートとVulkan機能を拡張し、AMD GPU向けにはROCm 10.0が提供される。新たに最新のx86-64プロセッサに最適化したamd64v3インストーラが用意されたほか、RVA23に対応する初のRISC-V向けデスクトップイメージ(SpacemiT K3ハードウェア対応含む)が登場した。RISC-V InternationalのCEOであるAndrea Galloは「2026年はRVA23シリコンの年であり、RISC-V向けデスクトップイメージのサポートが実現したことを嬉しく思う」と述べている。開発者向けには、Rust 1.97.1、OpenJDK 27、LLVM 22.1.6、GCC 15.2.0、Python 3.14.7、Go 1.27といったツールチェーンが更新され、AIワークロードの高速化にも対応が進んでいる。
