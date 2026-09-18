# WordPress用WooCommerceプラグインの脆弱性を悪用しPHPウェブシェル設置の攻撃が拡大
Tags: Security, OSS

- Attackers Exploit WooCommerce Wholesale Lead Capture Flaw to Plant PHP Web Shells (2026-09-16)
  https://thehackernews.com/2026/09/attackers-exploit-woocommerce-wholesale.html
- Hackers target WordPress sites via third-party WooCommerce plugin (2026-09-15)
  https://www.bleepingcomputer.com/news/security/hackers-target-wordpress-sites-via-third-party-woocommerce-plugin/
- PHP Webshell Campaign Targets WordPress Through Critical WooCommerce Plugin Bug (2026-09-16)
  https://www.infosecurity-magazine.com/news/woocommerce-wholesale-lead-capture/

6,000サイト以上で利用されているWordPressプラグイン「WooCommerce Wholesale Lead Capture」に、未認証の攻撃者がファイルをアップロードできる脆弱性(CVE-2026-27540、CVSS9.8)が存在し、wwlc_file_upload_handler経由でPHPウェブシェルを設置する攻撃が急増している。Wordfenceは10万件以上の攻撃を検知したと報告しており、今年2月にパッチが提供されていたにもかかわらず、多数のサイトが未更新のまま被害に遭っている。
