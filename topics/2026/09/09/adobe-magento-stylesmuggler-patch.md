# Adobe、Magentoの重大ゼロデイ「StyleSmuggler」(CVSS 10.0)に緊急パッチを公開
Tags: Security

- Adobe Patches Magento Zero-Day Exploited to Deploy Rust Backdoor and PHP Web Shell (2026-09-08)
  https://thehackernews.com/2026/09/adobe-patches-magento-zero-day.html
- Adobe Patches Over 170 Vulnerabilities, Including Commerce Zero-Day (2026-09-08)
  https://www.securityweek.com/adobe-patches-over-170-vulnerabilities-including-commerce-zero-day/
- Adobe fixes critical Magento zero-day exploited to backdoor servers (2026-09-08)
  https://www.bleepingcomputer.com/news/security/adobe-fixes-critical-magento-zero-day-exploited-to-backdoor-servers/

Adobeは、Magento Open SourceおよびAdobe Commerceに存在する最大深刻度(CVSS 10.0)のゼロデイ脆弱性CVE-2026-75650、通称「StyleSmuggler」に対する緊急パッチ(APSB26-146)を公開した。攻撃者は少なくとも9月4日から、決済失敗のリマインダーメール描画機能を悪用して認証不要でPHPコードを注入し、Rust製バックドアやPHP Webシェルを設置する攻撃を行っていた。Adobeは管理者に対しパッチ適用に加え、暗号鍵のローテーションや全認証情報のリセットも推奨している。
