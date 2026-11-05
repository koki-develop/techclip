# Debian/UbuntuのAPTに中間者攻撃でroot権限のコード実行を許す脆弱性(CVE-2026-109518)
Tags: Security, OSS

- Debian and Ubuntu APT Flaw Lets MitM Attackers Swap Verified Packages and Run Code as Root (2026-11-04)
  https://thehackernews.com/2026/11/debian-and-ubuntu-apt-flaw-lets-mitm.html
- CVE-2026-109518 APT vulnerability fixes available (2026-11-04)
  https://ubuntu.com/blog/apt-vulnerability-fixes-available
- Debian's APT Affected By Man-In-The-Middle Attack For Arbitrary Code Execution As Root (2026-11-04)
  https://www.phoronix.com/news/Debian-APT-MITM-RCE

DebianとUbuntuのパッケージマネージャAPTに、HTTPダウンロードの再試行処理に起因する脆弱性(CVE-2026-109518、CVSS 7.7)が発見された。HTTP通信を改ざんできる中間者攻撃者は、正規の.debパッケージを悪意あるものに差し替え、root権限で任意のコードを実行できる。Debian 12やUbuntu 22.04以降がデフォルトで影響を受け、Ubuntu 14.04から26.10まで広範なリリース向けに修正パッケージが提供された。CanonicalはHTTPSの利用などの緩和策も案内している。
