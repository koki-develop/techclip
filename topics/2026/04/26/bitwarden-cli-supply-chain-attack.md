# BitwardenのCLI npmパッケージがサプライチェーン攻撃で一時改ざん、開発者認証情報が窃取対象に
Tags: Security

- Bitwarden CLI Compromised in Ongoing Checkmarx Supply Chain Campaign (2026-04-23)
  https://thehackernews.com/2026/04/bitwarden-cli-compromised-in-ongoing.html
- Bitwarden CLI npm package compromised to steal developer credentials (2026-04-23)
  https://www.bleepingcomputer.com/news/security/bitwarden-cli-npm-package-compromised-to-steal-developer-credentials/
- Bitwarden NPM Package Hit in Supply Chain Attack (2026-04-23)
  https://www.securityweek.com/bitwarden-npm-package-hit-in-supply-chain-attack/

パスワードマネージャーBitwardenのCLI npmパッケージ（@bitwarden/cli@2026.4.0）が、Checkmarxが追跡するサプライチェーン攻撃キャンペーンの一環として一時的に改ざんされた。悪意のあるバージョンはGitHub/npmトークン、SSHキー、環境変数、クラウドシークレットなどを外部サーバーへ送信する機能を持ち、開発者環境に深刻なリスクをもたらした。
