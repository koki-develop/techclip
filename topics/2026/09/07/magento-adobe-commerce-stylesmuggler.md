# Magento/Adobe Commerceの未パッチゼロデイ「StyleSmuggler」が悪用、オンラインストアにバックドア設置被害
Tags: Security

- Unpatched Magento and Adobe Commerce Zero-Day Exploited to Backdoor Online Stores (2026-09-05)
  https://thehackernews.com/2026/09/unpatched-magento-and-adobe-commerce.html
- StyleSmuggler: Magento and Adobe Commerce 0-day RCE under active attack (2026-09-05)
  https://sansec.io/research/stylesmuggler
- Hackers Actively Exploiting Magento and Adobe Commerce 0-Day RCE Vulnerability (2026-09-05)
  https://cybersecuritynews.com/magento-and-adobe-commerce-0-day-rce/

オランダのセキュリティ企業Sansecが、Magento Open SourceおよびAdobe Commerceに存在する未パッチのゼロデイ脆弱性「StyleSmuggler」を発見した。認証不要でリモートコード実行が可能で、決済失敗のリマインダーメール描画時にPHPペイロードを注入し、NTP同期トラフィックを装ってC2通信を行うRust製バックドアを設置する二段階の攻撃手法が確認されている。パッチ済みの2.4.6-p15や最新の2.4.9を含む全バージョンが影響を受け、Adobeは9月6日時点でCVE番号もパッチも公表しておらず、実際の攻撃で既にオンラインストアへの侵害が進行している。
