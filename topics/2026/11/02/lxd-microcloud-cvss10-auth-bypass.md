# Canonical製LXD/MicroCloudに最大深刻度CVSS10.0の認証バイパス脆弱性
Tags: Security, OSS

- CVSS 10.0 LXD, MicroCloud Flaw Lets Attackers Impersonate Trusted Clients Without a Private Key (2026-11-01)
  https://thehackernews.com/2026/11/critical-lxd-and-microcloud-flaw-cvss.html
- Security advisory: Critical vulnerability found in Canonical LXD and MicroCloud (2026-10-28)
  https://discourse.ubuntu.com/t/security-advisory-critical-vulnerability-found-in-canonical-lxd-and-microcloud/90557
- LXD and Incus mTLS Authentication Bypass (CVE-2026-112816) (2026-11-01)
  https://blog.ostorlab.co/lxd-incus-mtls-authentication-bypass-cve-2026-112816.html

Canonicalが開発するコンテナ/VM管理ツールLXDおよびMicroCloud(同系統のIncusも対象)に、CVSS 10.0(最大深刻度)の脆弱性CVE-2026-112816が発見された。mTLS認証ロジックが証明書チェーンの有効性を適切に検証していなかったため、秘密鍵を持たない攻撃者が信頼済みクライアントの公開証明書を自身の証明書チェーンに付加するだけでroot権限相当のなりすましが可能だった。Canonicalは既に修正版をリリースしており、利用者には早急な適用が呼びかけられている。
