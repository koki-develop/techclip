# Azure Cosmos DBに深刻な脆弱性「CosmosEscape」、任意のデータベースへアクセス可能な状態に
Tags: Security, Cloud

- CosmosEscape: Azure Cosmos DB Flaw Exposed Platform-Wide Key That Could Access Any Database (2026-07-30)
  https://thehackernews.com/2026/07/azure-cosmos-db-flaw-exposed-platform.html
- CosmosEscape: Taking Over Every Database in Azure Cosmos DB (2026-07-30)
  https://www.wiz.io/blog/cosmosescape-taking-over-every-database-in-azure-cosmos-db
- Critical Flaw Led to Azure Cosmos DB Pwnage (2026-07-30)
  https://www.securityweek.com/critical-flaw-led-to-azure-cosmos-db-pwnage/

Wiz Researchが発見したAzure Cosmos DBの脆弱性「CosmosEscape」により、Gremlinクエリのサンドボックスを脱出してプラットフォーム全体の署名鍵を取得し、任意のテナントのデータベースへ完全な読み書きアクセスが可能な状態だったことが判明した。Microsoftは2026年7月中に恒久的な修正を全リージョンへ展開済みという。
