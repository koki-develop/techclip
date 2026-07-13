# 15年前から存在するLinuxカーネルの脆弱性「GhostLock」が発覚、ほぼ全ディストリビューションでroot権限奪取とコンテナエスケープが可能に
Tags: Security

- 15-Year-Old GhostLock Flaw Enables Root and Container Escape on Most Linux Distros (2026-07-08)
  https://thehackernews.com/2026/07/15-year-old-ghostlock-flaw-enables-root.html
- CVE-2026-43499 "GhostLock": 15-Year-Old Linux Kernel Flaw Gives Local Users Root Access and Container Escape — Public PoC Released (2026-07-08)
  https://threat-modeling.com/cve-2026-43499-ghostlock-linux-kernel-root-container-escape/

ロックの優先度継承処理にあるUse-After-Free脆弱性(CVE-2026-43499、CVSS 7.8)が2011年以降のほぼ全ての主要Linuxディストリビューションに存在し、ローカルユーザーが約5秒でroot権限を取得できることが判明した。Nebula SecurityがAIツール「VEGA」を用いて発見し、Googleから9万ドル超の報奨金を獲得しており、概念実証コードも公開されている。
