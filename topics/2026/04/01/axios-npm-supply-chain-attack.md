# axiosのnpmパッケージがサプライチェーン攻撃を受け、クロスプラットフォームRATを配布するバックドア入りバージョンが公開
Tags: Security, OSS

- Supply Chain Compromise of axios npm Package (2026-03-31)
  https://www.huntress.com/blog/supply-chain-compromise-axios-npm-package
- Axios Supply Chain Attack Pushes Cross-Platform RAT via Compromised npm Account (2026-03-31)
  https://thehackernews.com/2026/03/axios-supply-chain-attack-pushes-cross.html
- Axios npm packages backdoored in supply chain attack (2026-03-31)
  https://www.helpnetsecurity.com/2026/03/31/axios-npm-backdoored-supply-chain-attack/

人気JavaScriptライブラリ「axios」のメンテナーアカウントが乗っ取られ、バックドア入りの悪意あるバージョン（1.14.1・0.30.4）がnpmに公開された。これらのパッケージにはmacOS・Windows・Linux対応のリモートアクセストロイ（RAT）が仕込まれており、公開後89秒以内にCI/CDパイプライン経由での感染が確認されている。
