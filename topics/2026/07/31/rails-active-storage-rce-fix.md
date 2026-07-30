# Ruby on Rails、Active Storageの深刻な脆弱性を修正するセキュリティリリースを公開
Tags: Programming Languages, Security

- Rails Versions 7.2.3.2, 8.0.5.1, and 8.1.3.1 have been released! (2026-07-29)
  https://rubyonrails.org/2026/7/29/Rails-Versions-7-2-3-2-8-0-5-1-and-8-1-3-1-have-been-released

Ruby on Railsチームは、Active Storageの画像処理に起因する任意ファイル読み取り・リモートコード実行の脆弱性(CVE-2026-66066)を修正するセキュリティリリース(7.2.3.2/8.0.5.1/8.1.3.1)を公開した。libvipsの信頼できないローダーを起動時に無効化する対応が含まれ、利用者はlibvips 8.13以上へのアップデートも必要となる。
