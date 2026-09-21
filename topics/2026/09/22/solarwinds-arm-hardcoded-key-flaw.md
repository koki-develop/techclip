# SolarWinds Access Rights Managerにハードコード暗号鍵の脆弱性、認証なしRCEが可能(CVSS8.8)
Tags: Security

- SolarWinds Patches ARM Hard-Coded Key Flaw Enabling Unauthenticated RCE (2026-09-19)
  https://thehackernews.com/2026/09/solarwinds-patches-arm-hard-coded-key.html

SolarWindsのAccess Rights Manager(ARM 2026.2以前)にハードコードされた静的暗号鍵が存在し、認証なしでリモートコード実行が可能となる脆弱性(CVE-2026-28326、CVSS 8.8)が発見された。修正版のARM 2026.2.1が公開済みで、現時点では実悪用の報告はないものの、権限管理製品という性質上、悪用されれば影響範囲が大きいため早急なパッチ適用が推奨されている。
