# Docker Hubに重大な脆弱性、個人アクセストークンの不備で他ユーザーのコンテナイメージを改ざん可能と判明
Tags: Security

- Docker Hub flaw let attackers impersonate users, tamper with images (2026-10-13)
  https://www.bleepingcomputer.com/news/security/docker-hub-flaw-let-attackers-impersonate-users-tamper-with-images/

Docker Hubにおいて、個人アクセストークン(PAT)の不適切な再割り当てを利用し、攻撃者が他ユーザーになりすまして認証を突破できる脆弱性(CVE-2026-105445)が公表された。悪用されれば他ユーザーが管理するコンテナリポジトリへの不正アクセスやイメージの改ざんが可能だったとされ、Dockerは既に修正を行っている。
