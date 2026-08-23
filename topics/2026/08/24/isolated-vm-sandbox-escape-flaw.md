# JavaScriptサンドボックスライブラリisolated-vmに深刻な脆弱性、AIエージェント基盤にも影響
Tags: Security, OSS

- Isolated-vm Flaw Lets Sandboxed JavaScript Escape to Host for Potential RCE (2026-08-20)
  https://thehackernews.com/2026/08/isolated-vm-flaw-lets-sandboxed.html
- Critical Isolated-vm Vulnerability Leads to RCE on Host (2026-08-21)
  https://www.securityweek.com/critical-isolated-vm-vulnerability-leads-to-rce-on-host/
- Critical Flaw in isolated-vm Can Lead to Sandbox Escape, RCE Threat (2026-08-20)
  https://devops.com/critical-flaw-in-isolated-vm-can-lead-to-sandbox-escape-rce-threat/

n8nやMastra AIなどAI関連プロジェクトでも利用されるJavaScriptサンドボックスライブラリisolated-vmに、サンドボックス内コードがホストプロセスのメモリを破壊しリモートコード実行につながりうる型混同の重大な脆弱性が発見された。修正版が公開されており、影響を受けるプロジェクトには早急なアップデートが呼びかけられている。
