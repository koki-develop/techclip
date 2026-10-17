# Linuxカーネルの脆弱性「PwnEscape」、ゲストVMからホストのメモリ読み取りが可能と判明
Tags: Security

- Linux kernel gets a fix for a flaw that enabled attackers to escape VMs (2026-10-15)
  https://www.csoonline.com/article/4236460/linux-kernel-gets-a-fix-for-a-flaw-that-enabled-attackers-to-escape-vms.html
- Critical PwnEscape Linux Kernel Vulnerability Lets Guest VMs Read Host Memory (2026-10-15)
  https://thehackernews.com/2026/10/critical-pwnescape-linux-kernel.html

Linuxカーネルのネットワーク処理(チェックサムオフロード機能)に「PwnEscape」と呼ばれる脆弱性(CVE-2026-99999、CVSS9.3)が見つかった。ゲストVM内のコードがホストのカーネルメモリを読み取れ、root権限でのVMエスケープにつながる可能性がある。研究者Paulos Yibelo氏がVercelのサンドボックス環境で実証し、同社の100万ドル懸賞バグ報奨金プログラムを通じて発見した。マルチテナントのクラウド基盤に広く影響する可能性があるため、各社がパッチ適用を急いでいる。
