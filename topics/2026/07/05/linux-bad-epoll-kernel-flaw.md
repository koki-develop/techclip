# Linuxカーネルの新脆弱性「Bad Epoll」で一般ユーザーがroot権限取得可能、Androidにも影響
Tags: Security

- New "Bad Epoll" Linux Kernel Flaw Lets Unprivileged Users Gain Root, Hits Android (2026-07-04)
  https://thehackernews.com/2026/07/new-bad-epoll-linux-kernel-flaw-lets.html
- New "Bad Epoll" 0-Day Vulnerability Allows Root Access on Linux Servers and Android Devices (2026-07-04)
  https://cybersecuritynews.com/bad-epoll-0-day-vulnerability/
- Bad Epoll Vulnerability Lets Any Linux User Get Root (2026-07-04)
  https://latesthackingnews.com/2026/07/04/bad-epoll-vulnerability/

Linuxカーネルのepoll機能に新たなuse-after-free脆弱性「Bad Epoll」(CVE-2026-46242)が発見され、権限のない一般ユーザーがroot権限を取得できることが判明した。Linuxサーバーだけでなく大量のAndroid端末にも影響し、有効な回避策が存在しないため、各ディストリビューションでの緊急パッチ適用が急がれている。
