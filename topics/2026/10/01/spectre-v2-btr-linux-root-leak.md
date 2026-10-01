# 新型Spectre v2攻撃「Branch Target Reuse」、数分でLinuxのrootパスワードハッシュを漏洩
Tags: Security

- New Spectre v2 attack variant leaks Linux root password hash in minutes (2026-09-29)
  https://www.bleepingcomputer.com/news/security/new-spectre-v2-attack-variant-leaks-linux-root-password-hash-in-minutes/

研究者らは、Branch Target Reuse(BTR)と呼ばれる新型のSpectre v2攻撃(CVE-2026-64507、CVE-2026-64508)を実証した。Intelプロセッサ上でLinuxを実行するシステムにおいて、投機的実行の脆弱性を悪用することで、数分という短時間でrootパスワードハッシュを抽出できるという。既存の緩和策を回避する手法とされ、クラウド環境など多数のテナントが同一ハードウェアを共有する環境への影響が懸念されている。
