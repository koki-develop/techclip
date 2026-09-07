---
date: "2026-09-08T08:11:34+09:00"
title: "DHH氏が「職業人生最大のリリース」と語るLinux OS「Omarchy Quattro」、AIエージェントがOS設定からトラブルシューティングまで支援"
description: "Ruby on Railsの生みの親DHH氏が開発するArchベースのLinuxデスクトップOS「Omarchy」がフルスクラッチで刷新され、AIエージェントをOS操作に統合した「Omarchy Quattro」としてリリースされた。"
tags:
  - OSS
references:
  - "https://www.publickey1.jp/blog/26/dhhlinux_osomarchy_quattroaiosaios.html"
---

## 概要

Ruby on Railsの生みの親として知られるDavid Heinemeier Hansson（DHH）氏が開発するArchベースのLinuxデスクトップOS「Omarchy」が、8月14日にバージョン4.0にあたる「Omarchy Quattro」としてリリースされた。最大の特徴は、Claude、Codex、Copilot、Gemini、Grokといった複数のAIエージェントプラットフォームをOSの操作そのものに統合した点で、DHH氏自身はこのリリースを「職業人生を通じた最大級のソフトウェアリリース」と評している。あわせて、開発を支える「Omacom Foundation」の設立も発表された。

## 設計思想とAIエージェント統合

Omarchyは「Omacom」（Omakase Computing、おまかせコンピューティング)という思想に基づき、DHH氏が選び抜いた統一的な機能とビジュアルをあらかじめ組み込んで提供する点を特徴としてきた。Quattroではこの方針を踏襲しつつ、AIエージェントによるスキルファイル読み込みの仕組みを新設し、ユーザーがマニュアルを読まずに使い始められる体験を目指している。具体的には、アプリケーションのインストール、キーバインドの変更、タイル型ウィンドウマネージャ「Hyperland」やシェルフレームワーク「Quick Shell」の設定変更、テーマの切り替えといった操作をAIエージェントが代行する。さらに一歩進んだ機能として、「ポモドーロタイマーを作って」といった自然言語の要望に応じて、AIエージェントがカスタムテーマやQuickShellプラグインをその場で生成し、OSに追加することも可能になっている。アプリケーションがクラッシュした際には、AIエージェントがログを自動解析して原因を突き止め、修正方法を提示する機能もあり、これまでLinuxユーザーが自力で対応してきたトラブルシューティングの負担を軽減する狙いがある。

## 技術基盤とWindowsとの連携

技術的な土台はArch Linuxで、ウィンドウマネージャにHyperland、シェルフレームワークにQuick Shellを採用し、Tokyo Nightなど複数のテーマを標準搭載する。開発ツールとしてはFoot、Neovim、VSCode、Cursor、Docker、GitHub CLI、Chromiumなどをあらかじめ組み込んでおり、インストール後すぐに使い始められる構成となっている。ただし操作の中心はSuperキーを軸としたキーボードショートカットとシェル、タイル型ウィンドウマネージャであるため、主な想定ユーザー層はITエンジニアだ。WindowsとのデュアルブートやDocker VM上でのWindows実行に加え、Windows Hypervisor PlatformとQEMUを活用した「Try Omarchy for Windows」機能により、Windows環境からもOmarchyを試せるようにしており、Windowsユーザーの導入障壁を下げる工夫が図られている。

## 今後の展望

DHH氏は今回のリリースに合わせ、開発を継続的に支える組織として「Omacom Foundation」を設立したことを明らかにした。同財団にはマイケル・デル氏やジャック・ドーシー氏といった著名な起業家からの出資も集まっているという。「WindowsやMacを代替できるほど使いやすく美しいOS」という目標を掲げるOmarchyが、AIエージェントとの統合によってどこまで一般ユーザーの裾野を広げられるか、また開発者コミュニティにどのような影響を与えるかが今後の焦点となりそうだ。
