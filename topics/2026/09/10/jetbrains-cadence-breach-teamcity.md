# JetBrains、未パッチのTeamCity脆弱性を突かれ自社サービス「Cadence」が侵害される
Tags: Security

- Attackers Breached JetBrains Cadence via Unpatched TeamCity, Extracting AWS Credentials (2026-09-05)
  https://thehackernews.com/2026/09/attackers-breached-jetbrains-cadence.html
- JetBrains Cadence Breach: Attackers Exploit Unpatched TeamCity CVE-2026-63077 to Exfiltrate AWS Credentials and Source Code (2026-09-06)
  https://www.rescana.com/post/jetbrains-cadence-breach-attackers-exploit-unpatched-teamcity-cve-2026-63077-to-exfiltrate-aws-credentials-and-source-co

攻撃者は未パッチのTeamCity脆弱性CVE-2026-63077(CVSS 9.8)を悪用し、JetBrains自身のCI/CDサービス「Cadence」に侵入した。2024年のサーバーバックアップからAWS IAM認証情報やソースコード、設定ファイルなどが窃取されており、開発ツールを狙ったサプライチェーンリスクとして注目されている。
