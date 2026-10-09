# SonicWall、SMA1000アプライアンスのCVSS10.0認証前SSRF脆弱性にパッチ公開
Tags: Security

- SonicWall Patches CVSS 10.0 Pre-Authentication SSRF Flaw in SMA1000 Appliances (2026-10-07)
  https://thehackernews.com/2026/10/sonicwall-patches-cvss-100-pre.html
- SonicWall fixes pre-auth SSRF flaw in SMA 1000 appliances (CVE-2026-102255) (2026-10-07)
  https://www.helpnetsecurity.com/2026/10/07/sonicwall-fixes-pre-auth-ssrf-flaw-in-sma-1000-appliances-cve-2026-102255/
- SonicWall warns of max severity SSRF flaw in SMA1000 gateways (2026-10-07)
  https://www.bleepingcomputer.com/news/security/sonicwall-warns-of-max-severity-ssrf-flaw-in-sma1000-gateways/

SonicWallは、SMA1000シリーズ(6210、7210、8200v)のWorkPlaceインターフェースに存在するCVSS10.0の認証前SSRF脆弱性(CVE-2026-102255)を修正するパッチを公開した。同時にOSコマンドインジェクションやパストラバーサルなど追加の脆弱性3件にも対処している。現時点で悪用の証拠は確認されていないが、Shadowserverの調査では400台以上の露出機器が確認されており、管理者には早急なホットフィックス適用が推奨されている。
