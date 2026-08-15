---
date: "2026-08-15T20:02:43+09:00"
title: "中国系APT「Mustang Panda」、署名付きカーネルモードルートキットをバックドアCoolClientに統合"
description: "中国系ハッカー集団Mustang Panda（別名HoneyMyte）がバックドア「CoolClient」に署名付きのWindowsカーネルモードルートキットドライバを追加し、政府機関を標的とした攻撃でステルス性を大幅に強化していることが判明した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/08/mustang-panda-adds-signed-windows.html"
  - "https://securelist.com/honeymyte-coolclient-driver-rootkit/121028/"
  - "https://www.neowin.net/news/windows-rootkit-now-included-with-coolclient-backdoor-targeting-governments/"
---

## 概要

Kasperskyのセキュリティ研究者らは、中国系ハッカー集団Mustang Panda（別名HoneyMyte）が使用するバックドア「CoolClient」の新バージョンに、署名付きのWindowsカーネルモードルートキットドライバ（msagent.sys）が組み込まれていることを確認した。このドライバはプロセス、ファイル、レジストリキー、そしてC2（コマンド＆コントロール）通信のIPアドレスをOSレベルで隠蔽する機能を持ち、従来のエンドポイント保護製品による検出を著しく困難にする。被害はミャンマー、モンゴル、パキスタン、ロシアの政府機関を中心に確認されており、地政学的な諜報活動の一環とみられる。CoolClientは2022年にSophosが初めて報告したバックドアで、2023年にはTrend Microが分析を行っているが、今回のルートキット統合は同マルウェアにとって大きな機能拡張となる。

## 技術的な詳細

攻撃はまず、初期侵入用インプラント「PlugX」の展開から始まる。PlugXはCoolClientの各コンポーネントを配置するとともに、偽のインストールディレクトリをMicrosoft Defenderの除外対象に登録し、後続の検出を回避する。実行チェーンは多段階構成となっており、正規のSangfor実行ファイル（defender.exeにリネーム）が悪意あるDLL「libngs.dll」をサイドロードすることで開始する。このDLLが復号・実行する第2段階の「loadcert.ini」がpersistence（永続化）、UACバイパス、そしてルートキットドライバの展開を担当し、最終段階の「cert.ini」がC2通信を含むバックドア本体として機能する。

ルートキットドライバmsagent.sysは、CoolClientがService Control Managerへのアクセス権とSeTcbPrivilege特権を保持している場合にのみ展開される。このドライバは、Windowsのアクティブプロセスリストからエントリをアンリンクすることでプロセスを隠蔽するほか、ファイルシステムのミニフィルタで保護対象ファイルへのアクセスを拒否し、レジストリコールバックで保護対象キーを列挙対象から除外する。さらに、Nsiproxyドライバへのフックを通じて、設定されたC2のIPv4アドレスをネットワーク情報から除外し、通信の痕跡を隠す。ドライバは33種類のIOCTLハンドラを実装しているが、実際の攻撃で使用が確認されたのは、CoolClientを信頼済みプロセスとして登録する「0x222120」、C2のIPv4アドレスをドライバに渡す「0x2221E0」、保護対象のファイル・レジストリパスを登録する「0x2220F0」の3種類のみだった。

特に注目されるのは、このドライバが「Nanjing Ranyi Technology Co., Ltd.」名義で発行された、2013年8月から2014年9月まで有効期限が設定された古いデジタル証明書で署名されている点である。有効期限切れの古い証明書を悪用することで、署名検証を通過しつつ検出を回避する手口とみられる。永続化にはAutoRunレジストリエントリ「goopdate」やWindowsサービス「media_updaten」への登録、RPCベースのプロセス生成による親プロセスIDスプーフィング、synchost.exeへのプロセスインジェクションなど、複数の手法が組み合わされている。Kasperskyは、この設計が同グループが2025年12月に確認された「ToneShell」ルートキットと類似する点を指摘しつつ、CoolClient版は専用のIOCTLハンドラによりユーザーモードのバックドアと直接通信できる点で異なるとしている。

## 影響と今後の見通し

正規の署名証明書とカーネルレベルの隠蔽技術を組み合わせた今回の手口は、国家に支援された攻撃グループによるマルウェアの高度化が着実に進んでいることを示している。ルートキットによってプロセスやファイル、通信の痕跡がOSレベルで隠蔽されるため、フォレンジック調査や標準的なセキュリティ製品による検知が一段と難しくなる。Mustang Pandaは過去にもPlugXなどのツールで政府機関を継続的に標的としてきており、今回のアップデートは同グループが長期的な諜報活動においてステルス性の向上に注力し続けていることを裏付けている。
