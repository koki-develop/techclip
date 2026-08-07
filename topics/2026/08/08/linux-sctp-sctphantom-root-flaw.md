# 18年前から存在するLinuxカーネルのSCTP実装に深刻な脆弱性「SCTPhantom」、root権限奪取とコンテナエスケープが可能に
Tags: Security

- 18-Year-Old Linux SCTP Flaw Could Let Local Users Gain Root and Escape Containers (SCTPhantom) (2026-08-07)
  https://thehackernews.com/2026/08/18-year-old-linux-sctp-flaw-could-let.html

2008年から存在していたLinuxカーネルのSCTP実装におけるuse-after-free脆弱性(CVE-2026-64564、通称SCTPhantom)が公表された。Tencentの研究者はDebian 13やUbuntu 24.04などでroot権限奪取とコンテナエスケープに成功しており、既に8月3日リリースの安定版カーネルで修正済みとなっている。
