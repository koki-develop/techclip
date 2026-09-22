# WordPress CoreにCSRF脆弱性「Click2Shell」、悪意あるテーマ経由でRCEに発展の恐れ
Tags: Security, OSS

- WordPress Click2Shell flaw lets hackers execute PHP on the server (2026-09-21)
  https://www.bleepingcomputer.com/news/security/wordpress-click2shell-flaw-lets-hackers-execute-php-on-the-server/
- New WordPress Click2Shell Flaw Forces Theme Installs, Can Chain to Code Execution (2026-09-18)
  https://thehackernews.com/2026/09/new-wordpress-click2shell-flaw-forces.html
- Click2Shell: The RCE WordPress 7.1.1 Just Patched (2026-09-18)
  https://patchstack.com/articles/click2shell-the-rce-wordpress-7-1-1-just-patched/

WordPress Coreに「Click2Shell」と名付けられたCSRF脆弱性が発見された。管理者に細工したリンクをクリックさせるだけで悪意のあるテーマをインストールさせることができ、脆弱なテーマと組み合わせることでサーバー上での任意のPHPコード実行(RCE)に発展しうる。研究者Paulos Yibelo氏(pwn.ai)によると、サーバー側とフロントエンド側でのテーマスラッグ処理の不一致がjQueryセレクタインジェクションを引き起こす仕組みが原因という。WordPress 7.1.1で修正済みで、利用者には早急なアップデートが呼びかけられている。
