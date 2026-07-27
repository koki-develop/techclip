# Active Directory証明書サービスの脆弱性「Certighost」、ドメイン乗っ取り可能なPoCが公開
Tags: Security

- Certighost Exploit Lets Low-Privileged Active Directory Users Impersonate a Domain Controller (2026-07-24)
  https://thehackernews.com/2026/07/certighost-exploit-lets-low-privileged.html
- Certighost Active Directory CS Exploit Allows Low-Privileged Users to Compromise Domain (2026-07-24)
  https://cybersecuritynews.com/certighost-active-directory-cs-flaw/
- PoC Exploit Released for Critical AD CS Domain-Takeover Flaw "Certighost" (2026-07-27)
  https://www.helpnetsecurity.com/2026/07/27/certighost-cve-2026-54121-poc-exploit-released/

Active Directory証明書サービス(AD CS)の脆弱性「Certighost」(CVE-2026-54121、CVSS 8.8)により、低権限のドメインユーザーがドメインコントローラーになりすまし、DCSyncでkrbtgtハッシュを窃取できることが判明した。Microsoftは7月14日に修正済みだが、7月下旬に動作する概念実証コードが公開され、悪用リスクが高まっている。
