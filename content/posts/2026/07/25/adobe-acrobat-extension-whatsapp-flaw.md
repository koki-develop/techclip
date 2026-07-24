---
date: "2026-07-25T02:34:47+09:00"
title: "Adobe Acrobat拡張機能に「HermeticReader」脆弱性、3億台超でWhatsApp Web閲覧が可能に"
description: "3億台以上にインストールされているAdobe Acrobat Chrome拡張機能にUXSS脆弱性「HermeticReader」（CVE-2026-48294）が見つかり、悪意あるサイトを訪問するだけでWhatsApp Webのチャット内容が窃取される恐れがあったが、Adobeは既に修正版を配信済み。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/adobe-chrome-extension-flaw-let-sites-access-private-whatsapp-chats/"
  - "https://thehackernews.com/2026/07/adobe-acrobat-extension-flaw-let.html"
  - "https://www.securityweek.com/flaw-in-adobe-extension-with-300m-installs-enabled-whatsapp-data-theft/"
---

## 概要

世界で3億台以上にインストールされているAdobe Acrobat Chrome拡張機能に、セキュリティ企業Guardio Labsの研究者Nati Tal氏とShaked Biner氏によって「HermeticReader」と名付けられた脆弱性（CVE-2026-48294、CVSSスコア7.4）が発見された。この脆弱性はUXSS（ユニバーサルクロスサイトスクリプティング）に分類されるクロスオリジン情報漏洩の欠陥で、ユーザーが悪意あるWebサイトを訪問しただけで、バックグラウンドで開いていたWhatsApp Webのチャット履歴、連絡先名、メッセージのプレビュー、プロフィール情報などが第三者に窃取される恐れがあった。攻撃にはマルウェアや認証情報の窃取、セッションCookieへのアクセスも不要で、悪意あるページへの1回の訪問だけで成立する点が深刻とされている。影響を受けたのはバージョン26.5.2.2以前のAdobe Acrobat Chrome拡張機能で、Adobeは通知を受けてから週末を挟んで2日以内にバージョン26.5.2.3を自動配信し、修正を完了させた。悪用が確認された形跡はないという。

## 技術的な詳細

攻撃チェーンは複数の脆弱性を連鎖させる形で成立していた。まず、拡張機能が内部的に持つHTMLリソースが、本来は拡張機能専用であるにもかかわらず、任意のWebページからiframeとして読み込めるようになっていた。攻撃者はこのiframe経由で拡張機能の内部メッセージを偽装したコマンドを送り込み、拡張機能のローカルストレージに書き込みを行うことで、通常は休眠状態にある「Hermes」と呼ばれる統合エンジンを有効化できた。HermesはAcrobatとWhatsApp Webを橋渡しする機能で、これが有効化されると、攻撃者はバックグラウンドタブで開かれたWhatsApp WebのDOM(Document Object Model)を直接操作できるようになる。具体的には、WhatsApp Web上にPOSTフォームを注入し、value属性を持たないoption要素がそのテキスト内容を送信するというHTML仕様上の挙動を悪用して、表示中の全コンテンツを連結して送信させる手口が使われた。さらに、WhatsApp Web側にform-action CSP(Content Security Policy)ディレクティブが設定されていなかったため、このフォームは攻撃者が管理するサーバーへ自由に送信でき、コンテンツセキュリティポリシーによる防御も回避された。Guardio Labsはこの攻撃の様子を実演する動画を自社サイトで公開している。

## 影響と今後の展望

Chrome拡張機能はブラウザ内で高い権限を持つことが多く、今回のケースのように複数の脆弱性が連鎖することで、一見無関係なサービス(この場合はWhatsApp Web)の機密データが漏洩する経路が生まれ得ることを改めて示す事例となった。3億台超という導入規模の大きさから、パッチが行き渡るまでの期間中は広範なユーザーがリスクにさらされていたことになる。ユーザー側は特別な対応を取らずとも自動更新によって修正版が適用されるため、Chromeおよび拡張機能を最新の状態に保つことが重要となる。今回のような統合機能(他サービスとの連携エンジン)を持つ拡張機能については、開発元による内部通信の検証強化や、連携先サービス側でのCSP設定の徹底が今後の再発防止に求められる。
