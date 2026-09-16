---
date: "2026-09-16T18:14:05+09:00"
title: "中国系ハッカー2集団がChrome/Windowsのゼロデイ連鎖を共有、GRIMWEDGEでNGOを標的に"
description: "中国系の脅威アクターUTA0560とJungleBamboo（APT31）が、バイト単位で一致する同一のChrome/Windowsゼロデイ攻撃チェーンを用いて別々のバックドアを異なる標的に展開していたことが判明した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/china-linked-hackers-exploit-chrome.html"
  - "https://www.volexity.com/blog/2026/09/09/mind-the-patch-gap-multiple-chinese-threat-actors-chain-0-day-exploits-in-chrome-windows/"
  - "https://securityaffairs.com/199104/apt/one-exploit-chain-two-espionage-campaigns-chrome-and-windows-under-fire.html"
---

## 概要

セキュリティ企業Volexityは、中国系の脅威アクター2組が2026年9月1日から、同一のChrome/Windowsゼロデイ攻撃チェーンを使ってNGO組織を標的にしていたことを検出した。1組目の「UTA0560」はJavaScriptベースのバックドア「GRIMWEDGE」を、もう1組の「JungleBamboo」（中国のAPTグループAPT31の別名）は認証情報窃取用のChrome拡張機能「LONGTALE」（別名GemStone）を、それぞれ異なる標的に配布していた。両者が使用したシェルコードはバイト単位で完全に一致しており、共有のサプライチェーンないしエクスプロイト仲介業者の存在を示唆している。

## 攻撃の手口とエクスプロイトチェーン

攻撃は寄付を装ったルアーを用いたスピアフィッシングメールから始まる。メール内のリンクは米国の大学ウェブサイトに存在した反射型XSS脆弱性を悪用しており、受信者を攻撃者管理下のインフラへリダイレクトする。そこから「Files1.html → react.min.js → page.html」という3段階のローダーを経て、Base64エンコードされた3つのシェルコードコンポーネント（ホスト偵察用の「p1」、Windowsカーネル権限昇格用の「p2」、ブラウザプロセスへのコード注入とペイロードダウンロード用の「pp」)が展開される。

脆弱性チェーンはChromeのV8エンジンにおける型混同(CVE-2026-85046)を起点に、WebAssemblyの欠陥(CVE-2026-87491)でサンドボックスをエスケープし、最終的にWindowsカーネル/ALPCの脆弱性(CVE-2026-85880)でレンダラープロセスへのコード注入と権限昇格を実現するという3段構成になっている。GRIMWEDGEは250行に満たない軽量な実装ながら、情報収集・ファイル操作・プロセス管理・コマンド実行など10種類の機能を備え、「%COMPUTERNAME%」を基にしたホスト固有のビーコンで標的ごとに個別のペイロードを配信する。GRIMWEDGE自体には組み込みの永続化機構はないが、サイドローディング用のローダーwsc.dllがスケジュールタスクを作成して永続化を担う。一方JungleBambooはChromeのSecure Preferencesを改ざんしてレガシーなHMAC検証のフォールバックを悪用し、ローダーSUPERSTOMPを介して、Google Geminiを偽装したChrome拡張機能LONGTALEをインストール、キーロギングやクッキー・セッショントークンの窃取、キーワードを起点としたスクリーンショット取得など14種類のリモートコマンドを実行できる。

## 浮き彫りになった「パッチギャップ」問題

今回のキャンペーンが専門家の注目を集めているのは、悪用された脆弱性が「パッチギャップ」を突いていた点だ。該当の修正はChromiumのソースコードには8月4日の報告後に取り込まれていたが、Google Chromeの正式な安定版リリースには反映されていなかった。この結果、Chromiumレベルでは既知のNデイ脆弱性であるにもかかわらず、実際にChromeを利用するユーザーにとっては未パッチのゼロデイとして悪用可能な状態が生じていた。Volexityは、大規模言語モデルの活用が攻撃者側のエクスプロイト開発速度を加速させ、こうしたパッチギャップ脆弱性のリスクをさらに高めている可能性があると高い確信度で評価している。

## 対応状況と今後の展望

Googleは9月3日にChromeの正式パッチを配布し、CISAは翌9月4日にKnown Exploited Vulnerabilities(KEV)カタログへ本脆弱性チェーンを追加、連邦機関に対して9月18日までの対応を義務付けた。異なる攻撃者集団がバイト単位で同一のシェルコードを共有していた事実は、中国系APTの間でエクスプロイト開発やインフラが集中的に供給されている可能性を示しており、今後も同様の「パッチギャップ」を突く攻撃が繰り返される懸念がある。組織、とりわけ寄付キャンペーンなどで注目を集めやすいNGOは、Chromeやブラウザ関連ソフトウェアの迅速なアップデート適用と、フィッシングメール内リンクへの警戒を強めることが求められる。
