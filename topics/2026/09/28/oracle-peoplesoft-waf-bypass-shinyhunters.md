# ShinyHunters関連の攻撃者、WAFをバイパスしOracle PeopleSoftの脆弱性を悪用しWebシェル設置
Tags: Security

- Attackers Bypass WAFs to Exploit Oracle PeopleSoft Flaw and Deploy Web Shells (2026-09-26)
  https://thehackernews.com/2026/09/attackers-bypass-wafs-to-exploit-oracle.html
- ShinyHunters uses WAF bypass trick in Oracle PeopleSoft attacks (2026-09-26)
  https://www.bleepingcomputer.com/news/security/shinyhunters-uses-waf-bypass-trick-in-oracle-peoplesoft-attacks/
- ShinyHunters Renewed Mass Exploitation Campaign Targeting Oracle PeopleSoft (2026-09-25)
  https://cloud.google.com/blog/topics/threat-intelligence/shinyhunters-renewed-mass-exploitation-campaign-targeting-oracle-peoplesoft

恐喝集団ShinyHunters(GoogleはUNC6240として追跡)が、Oracle PeopleSoftの脆弱性CVE-2026-35273を悪用する大規模な再攻撃キャンペーンを展開していることが判明した。攻撃者は「P」を「%50」とURLエンコードするなどの手法でWAFの文字列一致ルールを回避し、世界各地のシステムにx.jspやu.jspといったWebシェル、SIDEEYEバックドアを設置している。Google MandiantのGTIGが技術詳細を公開し、対策を呼びかけている。
