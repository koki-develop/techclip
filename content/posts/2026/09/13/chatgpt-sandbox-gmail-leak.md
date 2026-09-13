---
date: "2026-09-13T18:35:45+09:00"
title: "ChatGPTのサンドボックスに共有『クリップボード』欠陥、Gmailデータが他アカウントへ漏洩可能に"
description: "Check Point Researchの調査により、ChatGPTのコード実行サンドボックスが内部のJFrog Artifactoryを介して分離を破られ、プロンプトインジェクションで他ユーザーのGmailデータを盗み出せる欠陥が発覚した。"
tags:
  - Security
  - AI
references:
  - "https://thehackernews.com/2026/09/chatgpt-flaw-let-planted-prompt-send.html"
  - "https://research.checkpoint.com/2026/the-shared-clipboard-inside-the-sandbox-cross-account-data-leakage-in-chatgpt/"
  - "https://thecyberexpress.com/chatgpt-sandbox-flaw-leads-to-gmail-leak/"
---

## 概要

Check Point Researchは9月8日、ChatGPTのコード実行サンドボックスに存在した欠陥を報告した。この欠陥を突くと、仕込まれたプロンプトインジェクションによって、あるユーザーのGmailデータを別ユーザーのChatGPTアカウントへ密かに送信できてしまう。問題の原因はAIモデル自体ではなく、ChatGPTが利用する内部インフラにあった。会話ごとに分離されているはずのコード実行コンテナが、パッケージ管理用に共有していた内部のJFrog Artifactoryインスタンスを介して、事実上つながってしまっていたのである。研究者はAlexey Bukhteyev氏で、2026年6月に脆弱性を特定し、OpenAIへ責任ある開示を行った上で9月8日に詳細を公表した。

## 脆弱性の仕組み

各会話用のコンテナはネットワーク的に相互分離されているものの、パッケージキャッシュとして共有のJFrog Artifactoryインスタンスにはすべてのコンテナからアクセスできた。研究者は、このArtifactoryのItem Management API――具体的には「Set Item Properties」でアイテムにメタデータを付与するエンドポイントと、「Get Storage Item Information」でそのメタデータを取得するエンドポイント――がアカウントごとに分離されていない点を突き止めた。あるアカウントから書き込んだテスト用プロパティを、別アカウントから読み出せることを実証し、これを「分離されているはずのコンテナ間の共有クリップボード」と表現している。

攻撃者はまず、チャットに仕込んだ隠しプロンプト、共有された会話リンク、あるいは隠し指示を含むカスタムGPTのいずれかの手段で、被害者のセッションに命令を植え付ける。すると、ChatGPTの「Thinking mode」が悪用され、ユーザーへの通常の応答を返す表の処理と、攻撃者の命令を実行する裏の処理が並行して走る。この裏側の処理でGmail、Google Drive、GitHub、Microsoft Teamsなど接続済みアプリからデータを読み取り、Artifactoryのメタデータ経由で攻撃者のアカウントへ密かに転送する。低リスクとみなされる読み取り操作は自動承認される仕様のため、ユーザーの目に触れるのは事後に表示される「Talked to Gmail」という小さなラベルのみで、実質的な確認や制御の機会は与えられなかった。研究者はこの手法で、実際に別々のアカウント間でGmailデータを移動させることに成功している。

## 影響とOpenAIの対応

流出しうるデータはGmailの内容にとどまらず、チャット履歴、アップロード済みファイル、セッションがアクセスできるあらゆるリソースに及ぶ。データはArtifactoryの共有メタデータ経由で持ち出されるため、通常のデータ損失防止(DLP)ツールでは痕跡を検知しにくい点も指摘されている。この脆弱性に対して個別のCVEは割り当てられていない。

OpenAIは問題のArtifactoryインスタンスを廃止することで対応した。この変更はサーバー側で完結するため、ユーザー側での対応や更新は不要だったという。なお対応の経緯については報道により説明が分かれており、The Hacker Newsは開示を受けての措置と伝える一方、The Cyber Expressは、別件のHugging Face関連インシデントを機に同インスタンスが廃止された結果、この欠陥も併せて解消されたと報じている。OpenAIは今回の開示に関する取材には応じていない。

## 背景と今後の展望

Check Pointによる同種の指摘はこれが初めてではなく、2026年3月にもDNSを利用したデータ持ち出し経路を報告しており、今回は共有インフラを起点とするクロスアカウント通信の欠陥として2件目となる。Check PointのPedro Drimel Neto氏は「AIセキュリティにおける最大のリスクは、我々がAIに与えているアクセス権と信頼そのものになった」と述べており、Check Pointは報告書の中で、外部サービスと連携するAIモデルを「強制されたインサイダー」になぞらえている。ChatGPTのようにGmailやGoogle Drive、GitHubなど機密性の高い外部サービスと連携するAIエージェントが増える中、モデルの安全性だけでなく、それを支える共有インフラの分離設計そのものが新たな攻撃対象になり得ることを示す事例といえる。
