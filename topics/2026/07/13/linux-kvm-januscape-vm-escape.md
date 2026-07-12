# Linuxカーネルに16年間潜んでいたKVM脆弱性「Januscape」が公表、ゲストVMからホストへの脱出が可能に
Tags: Security, Cloud/Infrastructure

- 16-Year-Old Linux KVM Flaw Lets Guest VMs Escape to Host on Intel and AMD x86 Systems (2026-07-07)
  https://thehackernews.com/2026/07/16-year-old-linux-kvm-flaw-lets-guest.html

Linuxカーネルのshadow MMUに約16年間潜んでいたuse-after-free脆弱性「Januscape」(CVE-2026-53359)が公表され、悪意あるゲストVMがホストのカーネルメモリを破壊しゲストからホストへのエスケープを可能にすることが判明した。IntelとAMDの両x86プラットフォームに影響し、クラウド事業者の仮想化基盤に広く関わる深刻な問題となっている。
