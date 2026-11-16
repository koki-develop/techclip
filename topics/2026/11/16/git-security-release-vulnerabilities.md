# Gitが6件の脆弱性を修正するセキュリティリリースを公開、再帰的クローンによるコード実行の欠陥に対処
Tags: OSS, Security

- Git Patches Flaw That Lets Malicious Repositories Execute Code During Recursive Clones (2026-11-10)
  https://thehackernews.com/2026/11/git-patches-flaw-that-lets-malicious.html
- Git security vulnerabilities announced (2026-11-10)
  https://github.blog/open-source/git/git-security-vulnerabilities-announced-7/

Gitプロジェクトが6件の脆弱性を修正したセキュリティリリース(v2.56.1など)を公開した。最も深刻な問題は再帰的クローン時に悪意あるリポジトリがサブモジュールのフックを悪用して任意コードを実行できるCVE-2026-111760で、リファレンス処理やマージ、バイナリパッチ、インポート機能に関わる問題も修正されている。v2.27.0以降の全サポートバージョンが対象で、早急な更新が推奨されている。
