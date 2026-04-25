---
date: "2026-04-26T02:18:39+09:00"
title: "OracleのProject Detroit、JVM内にV8とCPythonを統合してJava・Python・JSの相互呼び出しを実現へ"
description: "OracleがJavaOneで発表したProject DetroitがOpenJDKの公式プロジェクトとして進展し、JVM内からJavaScriptとPythonを直接呼び出せるようにする取り組みが本格化している。"
tags:
  - Programming Languages
references:
  - "https://www.infoworld.com/article/4145953/project-detroit-bridging-java-python-javascript-moves-forward.html"
---

## 概要

OracleはJavaOneカンファレンスにおいて、**Project Detroit**をOpenJDKコミュニティの公式イニシアチブとして正式に位置づけることを発表した。このプロジェクトは、JVM内にChromeのV8エンジン（JavaScript用）とCPythonランタイム（Python用）を直接組み込み、JavaからJavaScriptおよびPythonを直接呼び出せるクロスランゲージ・インタロップを実現することを目標としている。OracleのJavaプラットフォームグループ上級副社長であるGeorges Saab氏は「Detroitの主な利点は、業界最高水準のJavaとJavaScript、あるいはJavaとPythonを組み合わせた統合的な技術利用が可能になること」と述べている。

## 技術的な詳細

技術面では、`javax.script` APIをJavaScript向けにV8エンジンで、Python向けにCPythonで実装する形を採用する。JVMとネイティブランタイムの橋渡しにはJava 22以降で標準化された**Foreign Function & Memory（FFM）API**が活用される。Javaヒープとネイティブヒープを分離して実行することによりセキュリティを強化しつつ、既存のV8およびCPythonが持つパフォーマンス最適化の恩恵をそのまま受けられる設計となっている。完全な言語互換性を確保するためにそれぞれのオフィシャルランタイムを採用しており、独自の部分的実装に伴うメンテナンスコストを抑える狙いもある。

## 背景と経緯

Project Detroitの発想自体は2018年頃に、JavaScriptがJavaの機能を拡張するメカニズムとして最初に提案された。しかし一時は開発の勢いを失い停滞していた。近年、AIライブラリへのアクセスや多言語混在環境でのビジネスロジック記述といったニーズが急増したことで関心が再燃し、今回のOpenJDKプロジェクト化という形で息を吹き返している。

## 今後の展望

当面はJavaScriptとPythonのサポートを中心に開発が進む予定だが、ロードマップには将来的な追加言語対応も含まれている。Java開発者にとっては、まだJava向けの同等ライブラリが存在しないJavaScriptやPythonのエコシステム資産（特にAI・機械学習ライブラリ）へのアクセスが容易になるという直接的な恩恵が期待される。OpenJDKプロジェクトとして正式化されたことで、コミュニティを巻き込んだ開発の加速が見込まれる。
