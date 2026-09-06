# Google、実際に悪用されているChromeのV8ゼロデイ脆弱性を緊急修正
Tags: Security

- Google Releases Chrome Update to Patch Actively Exploited V8 Zero-Day (2026-09-03)
  https://thehackernews.com/2026/09/google-releases-chrome-update-to-patch.html
- Google warns of new Chrome zero-day flaw exploited in attacks (2026-09-04)
  https://www.bleepingcomputer.com/news/security/google-warns-of-new-chrome-zero-day-flaw-exploited-in-attacks/
- Google patches actively exploited Chrome zero-day (CVE-2026-85046) (2026-09-04)
  https://www.helpnetsecurity.com/2026/09/04/google-chrome-zero-day-cve-2026-85046/

Googleは9月3日のChrome Stableチャンネル更新で、V8エンジンに存在する型混同の脆弱性CVE-2026-85046（CVSS 8.8）を含む12件の脆弱性を修正した。細工されたHTMLページを閲覧するだけでサンドボックス内での任意コード実行が可能になるこの脆弱性は既に実際の攻撃で悪用されていることが確認されており、Googleはユーザーに対しChrome 152.0.7977.82/.83への早急なアップデートを呼びかけている。2026年に入って6件目の悪用済みChromeゼロデイとなる。
