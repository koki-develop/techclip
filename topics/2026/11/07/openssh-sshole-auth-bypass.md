# OpenSSHに緊急パッチ、長大パスワードで認証をバイパスできる「*sshole」脆弱性
Tags: Security

- OpenSSH Issues Emergency Fix for Flaw Letting Long Passwords Bypass SSH Auth on Alpine Linux (2026-11-05)
  https://thehackernews.com/2026/11/openssh-issues-emergency-fix-for-flaw.html
- OpenSSH Flaw Lets Attackers Log Into Password-Disabled Linux Accounts (2026-11-05)
  https://www.bleepingcomputer.com/news/security/openssh-flaw-lets-attackers-log-into-password-disabled-linux-accounts/

musl libcの`crypt()`関数の実装とOpenSSHのユーザー列挙対策が組み合わさることで、256〜1024バイトという長大なパスワードを送信すると、パスワード認証を無効化しているはずのアカウントにもログインできてしまう「*sshole」脆弱性が発覚した。主にAlpine Linuxなどmusl系ディストリビューションが影響を受け、OpenSSH 10.6p2とAlpine側のパッチが緊急リリースされた。
