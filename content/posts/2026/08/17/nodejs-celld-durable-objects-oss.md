---
date: "2026-08-17T08:01:43+09:00"
title: "Node.js生みの親Ryan Dahl氏、Durable ObjectsをCloudflareから解放するOSS「celld」を公開"
description: "Node.jsとDenoの生みの親Ryan Dahl氏が、Cloudflare Workers/Durable Objects互換のAPIを自前インフラでセルフホストできるオープンソース実装「celld」を公開した。"
tags:
  - OSS
  - Cloud
references:
  - "https://www.theregister.com/devops/2026/08/12/nodejs-creator-liberates-durable-objects-from-cloudflare-with-celld/5286954"
---

## 概要

Node.jsおよびDenoの生みの親であるRyan Dahl氏が、Cloudflare WorkersのDurable Objectsおよび関連JavaScript APIと互換性を持つ、自己ホスト型・分散型の実装「celld」を公開した。Dahl氏自身はこれを「セルフホスト可能な分散Durable ObjectsおよびWorkers実装」と説明しており、Cloudflareのインフラに縛られずに同様のアーキテクチャを独自のバックエンド上で運用できる点が最大の特徴となっている。celldはApache 2ライセンスで公開されており、JavaScriptおよびTypeScriptで書かれたコードを実行できる。

## 技術的な詳細

celldはRustとJavaScriptで実装されており、非同期ランタイムにはTokio Rustを採用している。ストレージバックエンドにはAmazon S3互換のオブジェクトストレージを利用する設計で、各celldオブジェクトはそれぞれ独自のSQLiteコピーを保持する。オブジェクトごとに単一スレッドで処理を行うことで、複雑な同時実行制御の問題を回避しているという。API面ではCloudflare WorkersおよびDurable ObjectsのJavaScript APIと互換性があり、理論上はWebAssemblyを介してRust、C/C++、Go、Zigで書かれたコードも実行可能とされる。

Durable Objectsのアーキテクチャは、Cloudflareのエンジニアであるケントン・ヴァーダ氏が考案したもので、celldの開発チームはこれを「分散システムに近年もたらされた最良のプリミティブの一つ」と高く評価し、自らの実装を同アーキテクチャへの「ラブレター」と表現している。従来のAWS Lambdaのようなサーバーレスモデルとは異なり、Durable Objectsのモデルは計算とデータを同じ場所に共存させることで、WebSocket APIを活用した低遅延の分散Webアプリケーションを可能にする。リアルタイムの共同編集やマルチプレイヤーゲーム、AIエージェントの構築といった用途に適しているとされる。

## コストを巡る主張の対立

Dahl氏の試算によれば、Cloudflare上で100個のアクティブなDurable Objectセルを稼働させると月額415ドルかかるのに対し、celldをDigitalOceanのS3互換バケットと8GBの仮想マシンで運用した場合は月額49ドルで実現できるという。これに対してCloudflareは異論を唱えており、オブジェクトが休止状態であれば月額コストは20.65ドルまで下がると反論している。

## 開発方針と今後の展望

celldのGitHubリポジトリでは、AI生成コードによるコントリビューションが禁止されている点も特徴的だ。開発チームは「コーディングエージェントは、大規模かつコンテキストの乏しい変更を送りやすくしてしまう」ことを理由に挙げている。記事では、Neonをはじめとする他のデータベースサービスプロバイダーも計算とデータを同じ場所に配置する同様のアプローチを進めていることに触れており、celldの登場はこうした実行環境の次の潮流を象徴する動きとも位置づけられている。
