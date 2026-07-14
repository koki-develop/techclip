# 難読化ツールJscrambler、npmパッケージが侵害されAI開発者ツールの認証情報を狙う情報窃取マルウェアが混入
Tags: Security, OSS

- Compromised jscrambler npm Release Drops Rust Infostealer During Install (2026-07-11)
  https://thehackernews.com/2026/07/compromised-jscrambler-8140-npm-release.html
- Hackers backdoor Jscrambler npm package with infostealer malware (2026-07-13)
  https://www.bleepingcomputer.com/news/security/hackers-backdoor-jscrambler-npm-package-with-infostealer-malware/
- Multiple Jscrambler Packages Impacted by Supply Chain Attack (2026-07-14)
  https://www.securityweek.com/multiple-jscrambler-packages-impacted-by-supply-chain-attack/

難読化ツールを提供するJscrambler社のnpmパッケージ(8.14.0以降の複数バージョン)が侵害され、Rust製の情報窃取マルウェアが混入した。侵入後はAWSやGitHubに加え、Claude DesktopやCursorなど開発者向けAIツールの認証情報を狙って窃取する点が特徴で、関連する複数のパッケージにも影響が及んでいる。
