# 「Java4Shell」脆弱性でJira・Jenkins・Keycloakなどに認証不要の深刻なRCEリスク(CVE-2026-114938)
Tags: Security

- Java4Shell: CVE-2026-114938 Enables Pre-Auth RCE in Jira, Jenkins, Keycloak (2026-11-18)
  https://thehackernews.com/2026/11/java4shell-cve-2026-114938-enables-pre.html
- Critical Java4Shell flaw allows RCE attacks on major Java applications (2026-11-17)
  https://www.bleepingcomputer.com/news/security/critical-java4shell-flaw-allows-rce-attacks-on-major-java-applications/
- How to Find, Mitigate, and Patch the Critical Java4Shell Flaw (CVE-2026-114938) Now (2026-11-17)
  https://blog.qualys.com/vulnerabilities-threat-research/2026/11/17/how-to-find-mitigate-and-patch-the-critical-java4shell-flaw-cve-2026-114938-now

AVX-512 VBMI対応のx86-64プロセッサ上で動作するOpenJDK(17.0.6以降)のBase64デコーダにメモリ破壊の欠陥「Java4Shell」(CVE-2026-114938)が見つかった。Jira、Jenkins、Keycloak、Confluence、JFrog Artifactory、PingFederateなど主要なエンタープライズJavaアプリケーションで認証不要の遠隔コード実行が可能になる深刻な脆弱性で、Oracleは2026年11月17日の月例セキュリティパッチで修正した。`-XX:-UseBASE64Intrinsics`フラグによる一時的な緩和策も案内されている。
