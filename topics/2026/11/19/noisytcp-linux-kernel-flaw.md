# 「NoisyTCP」、11年前からのLinuxカーネルTCP脆弱性でサーバーが無認証でクラッシュ可能に
Tags: Security, OSS

- New NoisyTCP Linux kernel flaw lets attackers crash servers (2026-11-16)
  https://www.bleepingcomputer.com/news/linux/new-noisytcp-linux-kernel-flaw-lets-attackers-crash-servers/

「NoisyTCP」と名付けられた脆弱性(CVE-2026-99288)が発見された。2015年に導入されたLinuxカーネルのTCP処理における競合状態由来のuse-after-freeが原因で、Nginx・Apache・SSHなど多数のサーバーソフトウェアが、認証なしの攻撃者によってクラッシュさせられる可能性がある。11年間潜在していた欠陥であり、影響範囲の広さが懸念されている。
