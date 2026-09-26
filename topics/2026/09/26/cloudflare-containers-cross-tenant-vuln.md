# Cloudflare、コンテナ間でディスクデータが漏洩する脆弱性を修正
Tags: Cloud, Security

- How Cloudflare addressed a cross-tenant data exposure vulnerability in Containers (2026-09-24)
  https://blog.cloudflare.com/containers-cross-tenant-vulnerability/
- Cloudflare Fixes Flaw That Let One Container Read Another Customer's Leftover Disk Data (2026-09-25)
  https://thehackernews.com/2026/09/cloudflare-fixes-flaw-that-let-one.html
- Cloudflare Containers Vulnerability Could Leak Data Between Customer Workloads (2026-09-25)
  https://cybersecuritynews.com/cloudflare-containers-vulnerability/

Cloudflareは、Containersのストレージ層で"skip_block_zeroing"設定の不備によりディスクブロックが完全に消去されず、削除済みコンテナが使用していたブロックを別テナントのコンテナが読み取れる脆弱性を修正したと発表した。悪用によりディレクトリ構造やSQLiteデータベースの断片など他テナントの残存データが漏洩する可能性があったが、実際の悪用は確認されていない。Cloudflareは該当設定の無効化、既存ディスクの廃棄、検知シグネチャの実装などの対応を完了したとしている。
