# 中国系ハッカー集団UNC3569、テンセントの入力アプリ「搜狗输入法」の脆弱性を悪用しGrayRabbitバックドアを展開
Tags: Security

- Hackers exploit Tencent app flaw to deploy GrayRabbit malware (2026-09-13)
  https://www.bleepingcomputer.com/news/security/hackers-exploit-tencent-app-flaw-to-deploy-grayrabbit-malware/
- China-Linked UNC3569 Exploited Sogou Input Method Flaw to Deploy GRAYRABBIT Backdoor (2026-09-11)
  https://thehackernews.com/2026/09/china-linked-unc3569-exploited-sogou.html
- Gray Rabbits and the Tale of a One-Click Backdoor (2026-09-10)
  https://www.gendigital.com/blog/insights/research/one-click-backdoor-sogou

中国と関連するハッキング集団UNC3569が、テンセント製の中国語入力アプリ「搜狗输入法(Sogou)」の脆弱性(CVE-2026-51990)を悪用し、GRAYRABBITバックドアを展開していたことが判明した。発見元のGen Digitalによると、プロトコルハンドラの引数検証不備、無制限URLナビゲーション、旧式Chromiumエンジンの3つの脆弱性を連鎖させたワンクリックRCEが用いられたという。テンセントはバージョン16.3.0.3498で修正したが、根本原因である旧式Chromiumエンジン自体の問題は未解決と指摘されている。同ソフトは中国で数億台にインストールされており、影響範囲は大きい。
