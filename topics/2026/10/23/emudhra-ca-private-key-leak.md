# eMudhra認証局の中間証明書で秘密鍵漏洩、ブラウザ各社とGo・Pythonが信頼拒否へ
Tags: Security, Programming Languages

- Mozilla, Google, Apple Block Compromised eMudhra CA Certificates (2026-10-20)
  https://www.bleepingcomputer.com/news/security/mozilla-google-apple-block-compromised-emudhra-ca-certificates/
- [security] Go 1.27.3 and Go 1.26.10 are released (2026-10-19)
  https://groups.google.com/g/golang-announce/c/66pojueaQek
- Python 3.15.1, 3.14.9 and 3.13.17 are out (2026-10-21)
  https://blog.python.org/2026/10/python-3151-3149-31317/

インドの認証局eMudhra(emSign)が発行した8枚の中間証明書で、2025年4月の鍵生成儀式の不備により秘密鍵が極めて脆弱な状態だったことが発覚した。MozillaやGoogle、Appleは該当証明書のブロックや信頼ルートからの削除といった緊急対応を行い、Go言語やPythonも最新リリースで該当証明書を強制的に信頼しないよう修正した。
