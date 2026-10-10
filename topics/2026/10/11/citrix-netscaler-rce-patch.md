# Citrix、NetScalerの深刻なRCE脆弱性(CVSS9.5)にパッチ公開、SAML構成環境が対象
Tags: Security

- Citrix warns admins to patch new NetScaler RCE flaw immediately (2026-10-09)
  https://www.bleepingcomputer.com/news/security/citrix-warns-admins-to-patch-new-netscaler-rce-flaw-immediately/
- Citrix gives NetScaler admins another critical reason to patch (2026-10-09)
  https://www.theregister.com/security/2026/10/09/citrix-gives-netscaler-admins-another-critical-reason-to-patch/5302212
- Citrix Patches Critical NetScaler Flaw That Could Enable RCE in SAML Deployments (2026-10-09)
  https://thehackernews.com/2026/10/citrix-patches-critical-netscaler-flaw.html

CitrixはNetScaler ADC/GatewayのうちSAMLのIdPまたはSPとして構成された環境に影響する、メモリオーバーフローに起因する深刻な脆弱性CVE-2026-107406(CVSS9.5)を修正するパッチを公開した。この脆弱性はリモートコード実行またはサービス拒否を招く恐れがあるが、同社は現時点でこの脆弱性が実際に悪用された証拠はないとしている。NetScalerでは今月に入り複数の脆弱性が相次いで報告されており、管理者には早急なパッチ適用が求められている。
