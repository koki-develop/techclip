# Elixir向けパッケージレジストリhex.pmで遠隔コード実行攻撃、機密情報への不正アクセスの可能性
Tags: Security, OSS

- Security incident on hex.pm (2026-11-24)
  https://hex.pm/blog/security-incident-on-hexpm

Elixir/Erlang向けパッケージレジストリhex.pmで、リクエストデコーダの脆弱性(CVE-2026-129514)を突いた遠隔コマンド実行攻撃が11月23日に発生した。運営チームは20分以内に攻撃を遮断し修正を適用したが、メールアドレスやパスワードハッシュなどの機密情報への不正アクセスを完全には否定できないとしている。
