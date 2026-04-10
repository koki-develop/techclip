# Docker Engine 29.4.0リリース、複数のセキュリティ脆弱性を修正しBuildKit v0.29.0を搭載
Tags: OSS, Security

- Docker Engine 29.4.0 release notes (2026-04-03)
  https://docs.docker.com/engine/release-notes/29/

Docker Engine 29.4.0がリリースされ、BuildKitのGit URLバリデーション不備（CVE-2026-33748）やAuthZプラグインのバイパス（CVE-2026-34040）など複数のセキュリティ脆弱性が修正された。containerd v2.2.2、Go 1.25.8、BuildKit v0.29.0へのアップデートやレジストリ接続のHTTP keep-alive有効化によるイメージpull/push性能改善も含まれる。
