# Kaltura配布の動画プレーヤーmwEmbedに未修正の重大脆弱性、認証なしでファイル読み取り・RCEが可能に
Tags: Security

- Unpatched Kaltura mwEmbed Flaws Could Let Remote Attackers Read Files and Run Code (2026-08-26)
  https://thehackernews.com/2026/08/unpatched-kaltura-mwembed-flaws-could.html
- VU#308749 - Remote Code Execution and Arbitrary File Read Vulnerabilities in Kaltura Servers (2026-08-25)
  https://kb.cert.org/vuls/id/308749

CERT/CCが、Kaltura配布のHTML5動画プレーヤーライブラリmwEmbed(html5lib)に存在する未修正の脆弱性CVE-2026-19912およびCVE-2026-19913を公表した。mwEmbedLoader.phpエンドポイントの安全でないデシリアライゼーションに起因し、認証なしでサーバー上の任意ファイル読み取りやリモートコード実行が可能になる。CERT/CCはKaltura社に再三連絡を試みたが応答が得られておらず、パッチが未提供のまま技術的詳細が公開された形となり、同ライブラリを組み込んだ多数のサイトに影響が及ぶ懸念がある。
