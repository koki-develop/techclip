# Linuxカーネルに12年前からの脆弱性「NFS2ROOT」、NFSサーバー経由でroot権限奪取が可能に
Tags: Security

- New NFS2ROOT Linux flaw can let attackers gain root privileges (2026-11-27)
  https://www.bleepingcomputer.com/news/security/new-nfs2root-linux-flaw-can-let-attackers-gain-root-privileges/

Linuxカーネルのネットワークファイルシステム(NFS)サーバー実装に、12年前から存在していた重大な脆弱性「NFS2ROOT」(CVE-2026-99362)が発見された。リモートの攻撃者がこの欠陥を悪用することで、NFSサーバーを経由してホスト上のroot権限を奪取できる可能性がある。長年見過ごされてきたカーネルコンポーネントの欠陥であり、NFSを利用する多数のLinux環境に影響が及ぶとみられる。
