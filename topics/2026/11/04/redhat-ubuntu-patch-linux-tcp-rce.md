# Red Hat・UbuntuがLinuxカーネルのCVSS9.8脆弱性(CVE-2026-98432)に正式パッチを公開
Tags: Security

- Red Hat Patches 9.8-Rated Linux TCP RCE Flaw While Ubuntu Releases Fixes for Testing (2026-11-03)
  https://thehackernews.com/2026/11/red-hat-patches-98-rated-linux-tcp-rce.html
- CVE-2026-98432: A Remote Use-After-Free in the Linux Kernel's TCP Stack (2026-11-02)
  https://www.akamai.com/blog/security-research/cve-2026-98432-remote-uaf-linux-kernels-tcp-stack

LinuxカーネルのIPv4 TCP処理に存在するuse-after-free脆弱性CVE-2026-98432(CVSS9.8)について、Red HatはRHEL 8/9/10向けに修正済みカーネルを公開し、UbuntuもLTS向けにテスト版の修正を提供した。この脆弱性は10月30日の発覚当初、AnthropicのAIモデルがMPTCPリスナーを持つサーバーに対し約53分で自律的にroot権限のリモートコード実行を達成したことで注目されたが、主要ディストリビューションでは修正が追いついていなかった。Akamaiのセキュリティチームも、TCPハンドシェイク処理中にIPv4オプションが解放された後に読み取られる仕組みを技術的に解説し、パッチ適用済みカーネルへの更新やMPTCP無効化などの緩和策を推奨している。
