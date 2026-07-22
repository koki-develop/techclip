# SharePointの重大RCE脆弱性が実際に悪用されマシンキー窃取、長期アクセスの温床に
Tags: Security

- Critical SharePoint RCE flaw exploited to steal machine keys (2026-07-21)
  https://www.bleepingcomputer.com/news/security/critical-sharepoint-rce-flaw-exploited-to-steal-machine-keys/
- Critical SharePoint RCE CVE-2026-50522 Under Active Exploitation After Public PoC (2026-07-22)
  https://thehackernews.com/2026/07/critical-sharepoint-rce-cve-2026-50522.html
- Another SharePoint RCE exploited: Patch, then rotate your machine keys (CVE-2026-50522) (2026-07-22)
  https://www.helpnetsecurity.com/2026/07/22/sharepoint-cve-2026-50522-exploited/

攻撃者はSharePoint Serverの脆弱性CVE-2026-50522(CVSS 9.8)を、公開PoC公開直後から悪用し始めていることがwatchTowrの調査で判明した。オンプレミスのSharePointサーバーからIISマシンキーを窃取して長期的なアクセスを維持する手口が確認されており、専門家はパッチ適用だけでなく認証情報のローテーションも推奨している。
