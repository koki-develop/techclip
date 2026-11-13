# Check PointゲートウェイがPHP2Shellで侵害され、VMware ESXiにワイパー展開
Tags: Security

- Check Point gateways hacked via PHP2Shell to deploy VMware ESXi wiper (2026-11-13)
  https://www.bleepingcomputer.com/news/security/check-point-gateways-hacked-via-php2shell-to-deploy-vmware-esxi-wiper/
- PHP2Shell Exploitation on Check Point Gateway (2026-11-12)
  https://research.checkpoint.com/2026/php2shell-exploitation-on-check-point-gateway/
- PHP2Shell Exploited in Destructive Check Point Gateway Attacks (2026-11-13)
  https://www.securityweek.com/php2shell-exploited-in-destructive-check-point-gateway-attacks/

未認証のリモートコード実行を可能にするPHPの重大な脆弱性「PHP2Shell」(CVE-2026-109618/109619)と、Check Point Security Gatewayのゼロデイ(CVE-2026-123039)を組み合わせた攻撃が確認された。攻撃者はMobile Accessポータル経由で侵入してroot権限を奪取し、バックドア「TSGA」を設置した後、VMware ESXiホストにデータ消去型マルウェア(ワイパー)を展開した。中国系脅威アクター「PhiliKit」との関連が指摘されている。
