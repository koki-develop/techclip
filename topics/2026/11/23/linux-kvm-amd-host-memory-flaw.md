# LinuxのKVMハイパーバイザーに新脆弱性、AMDホストでゲストVMがホストメモリ最大127GBに読み書き可能に
Tags: Security

- New Linux KVM Flaw (CVE-2026-99312) Lets Guest VMs Access Host Memory on AMD Hosts (2026-11-20)
  https://thehackernews.com/2026/11/new-linux-kvm-flaw-cve-2026-99312-lets.html
- Virtualization, Responsible Disclosure, and CVE-2026-99312 (2026-11-19)
  https://www.digitalocean.com/blog/cve-2026-99312-kvm-patch
- CVE-2026-99312: Linux KVM Flaw Let a Guest VM Read 127 GB of Host Memory on AMD Hosts (2026-11-20)
  https://dev.to/etairos/cve-2026-99312-linux-kvm-flaw-let-a-guest-vm-read-127-gb-of-host-memory-on-amd-hosts-4460

AMDプロセッサ上でネストした仮想化を有効にしたLinux KVMハイパーバイザーに、ゲストVMのrootユーザーがホストの物理メモリを最大127GBまで読み書きできる脆弱性(CVE-2026-99312)が見つかった。原因は2022年のセキュリティパッチで導入されたuse-after-freeバグで、INITリセット時にネストしたVMのページテーブルポインタが正しく復元されず、解放済みメモリを参照し続けてしまう。DigitalOceanのバグバウンティ経由でTerra Securityの研究者が発見し、責任ある開示を経て11月18日に修正済みカーネル(7.3.5、6.18.64、6.12.118)が公開された。多くのディストリビューションでは未適用のままで、ネスト仮想化の無効化が当面の緩和策となる。
