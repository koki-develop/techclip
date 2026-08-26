# OpenSSL 4.0.2公開、CMSやDTLS・QUICなど複数コンポーネントの脆弱性を修正
Tags: OSS, Security

- OpenSSL 4.0.2 Patches Multiple Security Flaws Across Core Components (2026-08-26)
  https://www.opensourceforu.com/2026/08/openssl-4-0-2-patches-multiple-security-flaws-across-core-components/

OpenSSL 4.0.2が公開され、CMSの鍵アンラップ処理におけるヒープバッファオーバーフローやDTLSレコードバッファリングでの過剰メモリ消費、QUICサーバーの不具合、OCSP・CMPの処理問題など複数コンポーネントにわたる脆弱性を修正した。保守対象の3.xブランチ(3.6.4、3.5.8、3.4.7、3.0.22)にも並行してセキュリティパッチが提供されている。
