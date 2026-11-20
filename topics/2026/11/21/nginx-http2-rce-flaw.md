# NGINXのHTTP/2処理に10年来の重大な脆弱性、未認証でのリモートコード実行が可能に
Tags: Security

- Rapid7 discloses a critical vulnerability affecting NGINX HTTP/2 that can lead to remote code execution (2026-11-18)
  https://www.rapid7.com/blog/post/ve-cve-2026-123007-critical-nginx-http-2-integer-underflow-leads-to-rce-fixed/
- 10-Year-Old NGINX HTTP/2 Flaw Lets Unauthenticated Attackers Execute Code on Servers (2026-11-18)
  https://thehackernews.com/2026/11/10-year-old-nginx-http2-flaw-lets.html
- Critical NGINX 'NGINX2Root' bugs let attackers hijack servers (2026-11-19)
  https://www.bleepingcomputer.com/news/security/critical-nginx-nginx2root-bugs-let-attackers-hijack-servers/

Rapid7とF5が、NGINXのHTTP/2フローコントロール処理に存在する10年来の整数アンダーフロー脆弱性(CVE-2026-123007、CVSS 9.2)を公開した。未認証の攻撃者がワーカープロセスのメモリを破壊し、nginxの権限で任意コードを実行できる恐れがある。ASLRのバイパスを伴う実証に加え、Linuxカーネルの別の欠陥と連鎖させることでDockerコンテナからホストへのエスケープとroot権限奪取も確認されたと報じられている。修正版のnginx 1.31.9・1.30.7が同日公開された。
