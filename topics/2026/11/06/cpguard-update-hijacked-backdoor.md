# cPGuardの自動更新機能が乗っ取られ、約2950台のLinuxサーバーにバックドアとパスワードハッシュ窃取スクリプトが配布される
Tags: Security

- cPGuard Update Channel Hijacked to Backdoor Linux Servers and Collect Password Hashes (2026-11-03)
  https://thehackernews.com/2026/11/cpguard-update-channel-hijacked-to.html
- Hackers hijack cPGuard autoupdate to deploy backdoor, steal data (2026-11-03)
  https://www.bleepingcomputer.com/news/security/hackers-hijack-cpguard-autoupdate-to-deploy-backdoor-steal-data/

セキュリティツールcPGuardの自動更新基盤が、盗まれた認証情報を使って侵害された。バージョン5.88.12から5.88.19を通じて悪意あるコードが配布され、攻撃者は更新の署名鍵を窃取したうえで、約2,950台の顧客Linuxサーバーにバックドアと認証情報窃取スクリプトを展開していた。収集された情報には/etc/shadowのパスワードハッシュやSSH鍵などが含まれており、サプライチェーン攻撃としての影響の大きさが懸念されている。
