# AhsayCBSの未修正脆弱性を連鎖悪用、Microsoft Edgeを偽装したXMRigマイナーとWebシェルを展開する攻撃が発生
Tags: Security

- Threat Actors Exploit Critical AhsayCBS Flaws to Drop Webshells and XMRig Cryptominer (2026-10-08)
  https://www.huntress.com/blog/ahsaycbs-flaws-exploit
- Unpatched AhsayCBS Vulnerabilities Exploited in the Wild (2026-10-09)
  https://www.securityweek.com/unpatched-ahsaycbs-vulnerabilities-exploited-in-the-wild/
- Attackers Exploit AhsayCBS Flaws to Deploy XMRig Miners Disguised as Microsoft Edge (2026-10-09)
  https://thehackernews.com/2026/10/attackers-exploit-ahsaycbs-flaws-to.html

セキュリティ企業Huntressは、バックアップ製品AhsayCBSに存在する未修正の認証バイパス(CVE-2026-105133)とOSコマンドインジェクション(CVE-2026-105134)を連鎖させた攻撃が実環境で行われていることを確認した。攻撃者はこれらの脆弱性を悪用してWebシェルを設置し、Microsoft Edgeを装ったXMRigクリプトマイナーを展開、さらに不正なWindowsサービスを用いて永続化を図っているという。パッチが未提供のため、同製品の利用組織には注意が呼びかけられている。
