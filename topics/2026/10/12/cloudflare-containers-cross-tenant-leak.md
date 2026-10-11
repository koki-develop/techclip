# Cloudflare、Containersのディスク未初期化が原因のクロステナントデータ漏えいを公表
Tags: Cloud, Security

- Cloudflare discloses cross-tenant data exposure in Containers platform (2026-10-05)
  https://www.infoq.com/news/2026/10/cloudflare-cross-tenant-exposure/

Cloudflareは、コンテナプラットフォームで新規割り当てされたディスクブロックをゼロ初期化しない設定が原因で、他顧客のデータ(DBページやSQLiteファイルなど)が読み取れる脆弱性を公表した。悪用の証拠はないとしつつ、発見から数時間で設定を修正し、9月19日までに全面対応を完了したと説明している。
