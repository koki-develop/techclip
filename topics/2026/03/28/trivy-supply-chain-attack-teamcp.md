# TeamPCPグループによるTrivyサプライチェーン攻撃の詳細と対策をMicrosoftが公開
Tags: Security, OSS

- Guidance for detecting, investigating, and defending against the Trivy supply chain compromise (2026-03-24)
  https://www.microsoft.com/en-us/security/blog/2026/03/24/detecting-investigating-defending-against-trivy-supply-chain-compromise/
- TeamPCP Compromises Telnyx Python Package on PyPI with Credential-Harvesting Malware (2026-03-27)
  https://thehackernews.com/

Microsoftのセキュリティブログは、AquaセキュリティのオープンソーススキャナーTrivyを標的にした大規模なサプライチェーン攻撃に関する検出・調査・防御のガイダンスを公開した。TeamPCP（別名DeadCatx3）グループによるこの攻撃では76のバージョンタグが悪意あるコミットに書き換えられ、CI/CDシークレットの窃取や持続的バックドアが仕掛けられており、同グループはさらにPyPIのtelnyx Pythonパッケージへの侵害も行っている。
