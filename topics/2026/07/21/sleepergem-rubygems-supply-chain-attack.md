# 休眠中のRubyGemsメンテナーアカウントが乗っ取られ、サプライチェーン攻撃「SleeperGem」が発覚
Tags: Security, OSS

- SleeperGem: RubyGems supply chain attack targets dormant maintainer accounts (2026-07-14)
  https://www.aikido.dev/blog/sleepergem-rubygems-supply-chain-attack
- SleeperGem Uses Three Malicious RubyGems Packages to Target Developer Machines (2026-07-20)
  https://thehackernews.com/2026/07/sleepergem-uses-three-malicious.html

6〜7年間休眠していたRubyGemsのメンテナーアカウント2件が乗っ取られ、git_credential_managerなど信頼されたパッケージに悪意あるコードが注入された「SleeperGem」攻撃が発覚した。CI環境を避けて開発者のマシンを直接狙う手口が特徴で、RubyGemsエコシステムにおける初の大規模サプライチェーン攻撃事例とされる。
