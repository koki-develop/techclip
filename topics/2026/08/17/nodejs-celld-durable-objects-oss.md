# Node.js生みの親Ryan Dahl氏、CloudflareのDurable Objectsを自前ホスト可能にするOSS「celld」を公開
Tags: OSS, Cloud

- Node.js creator liberates Durable Objects from Cloudflare with celld (2026-08-12)
  https://www.theregister.com/devops/2026/08/12/nodejs-creator-liberates-durable-objects-from-cloudflare-with-celld/5286954

Node.jsおよびDenoの生みの親であるRyan Dahl氏が、Cloudflare WorkersのDurable Objectsと互換性のあるAPIを自前のVM上でセルフホストできるオープンソースツール「celld」を公開した。SQLiteとS3互換ストレージのみで動作し、別途コンセンサスサービスを必要としない設計により、Cloudflareより低コストな運用を実現するとしている。
