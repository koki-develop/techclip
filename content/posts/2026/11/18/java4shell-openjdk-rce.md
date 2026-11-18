---
date: "2026-11-18T18:09:22+09:00"
title: "OpenJDKのBase64処理に認証不要RCEの欠陥「Java4Shell」、Jira・Jenkins・Keycloakなど主要製品が対象に"
description: "AVX-512 VBMI対応CPU上のOpenJDKに潜むメモリ破損の欠陥「Java4Shell」(CVE-2026-114938)により、Jira・Jenkins・Keycloakなど主要なエンタープライズJava製品で認証不要のリモートコード実行が可能になることが判明した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/11/java4shell-cve-2026-114938-enables-pre.html"
  - "https://www.bleepingcomputer.com/news/security/critical-java4shell-flaw-allows-rce-attacks-on-major-java-applications/"
  - "https://blog.qualys.com/vulnerabilities-threat-research/2026/11/17/how-to-find-mitigate-and-patch-the-critical-java4shell-flaw-cve-2026-114938-now"
---

## 概要

OpenJDKのハードウェア高速化Base64デコーダに、メモリ破損を引き起こす深刻な欠陥「Java4Shell」(CVE-2026-114938)が見つかった。AVX-512 VBMI命令対応のx86-64プロセッサ上で動作するOpenJDK 17.0.6以降（バージョン21、25、27を含む）が対象で、「=」で終わる末尾を細工した不正なBase64文字列をデコードさせると、デコーダが出力バッファの境界を62〜63バイト超えて書き込んでしまう。研究者らはこの挙動を悪用し、隣接する配列を操作して任意のメモリを読み書きする手法を「JavaBleed」と名付けた。影響は深刻で、Keycloak、Atlassian Jira、Atlassian Confluence、JFrog Artifactory、Jenkins、PingFederateといった認証基盤・開発ツールでは、ログインすら不要でリモートコード実行が可能になることが実証されている。Apache Kafka Broker、Apache Solr、Elasticsearch、Gerrit、Spinnakerなども認証済みの状態であれば同様に悪用され得る。

## 発見の経緯と深刻度評価

発見したのはセキュリティ企業CalifのQuang Luong氏で、OpenAIのコーディング支援ツール「Codex」を使い、約1時間で脆弱性を特定し、さらに2時間でエクスプロイトを完成させたという。深刻度の評価は評価者によって幅があり、CalifはCVSS 4.0で9.2(Critical)、Oracleは自社基準のCVSS 3.1で8.1(High)とした一方、Red Hatは予備評価でCVSS 9.8としている。悪用の引き金となる不正な入力自体は、2026年9月9日にOpenJDKのプルリクエスト上で一度公開されていたが、そのPRはマージされずに閉じられていた経緯があり、水面下で長く見過ごされていたリスクだったことがわかる。なお、カナダのサイバーセキュリティセンターは報道時点で実際の悪用を確認しておらず、CISAの既知の悪用脆弱性(KEV)カタログにも登録されていない。

## 対象範囲とハードウェア要件

脆弱性が成立するには、Javaのバージョンとプロセッサの両条件が揃う必要がある。対象となるJava環境はOpenJDK 17.0.6以降（21、25、27を含む）およびJava SE 8 Performance Pack(8u511b33-perf)、一部のGraalVMで、Oracle Java SE、Amazon Corretto、Eclipse Temurin、Microsoft Build of OpenJDK、Azul Zulu、Red Hat OpenJDKなど主要ディストリビューションが広く含まれる。標準のJava 8および11は対象外だ。プロセッサ側の条件は、AVX-512 VBMIをサポートするx86-64チップに限られ、具体的にはIntel XeonのIce Lake以降（Sapphire Rapids、Emerald Rapids、Granite Rapids）、AMD Zen 4以降のEPYC/Ryzenが該当する。ARM64アーキテクチャや、AVX-512 VBMIを搭載しないx86-64プロセッサは影響を受けない。

## 修正と緩和策

Oracleは2026年11月17日の月例セキュリティパッチで本脆弱性を含む655件の脆弱性に対応し、Java 8 Enterprise Performance Pack向けに8u513-perf、Java 17向けに17.0.21.1、Java 21向けに21.0.13.1、Java 25向けに25.0.5.1、Java 27向けに27.0.1.1をそれぞれリリースした。パッチ適用までの一時的な緩和策としては、JVM起動時に`-XX:-UseBASE64Intrinsics`フラグを付与し脆弱なコードパスのみを無効化する方法が推奨されている。より広範にAVX-512命令全体を無効化する`-XX:UseAVX=2`フラグも代替案として案内されているが、他の最適化にも影響するため性能面のトレードオフがある。対応の優先順位としては、インターネットに公開されたIDプロバイダ、同様に公開されたビルド・コラボレーションツール、その他の外部公開Javaサービス、最後に内部システムという順で緩和・パッチ適用を進めることが推奨されている。
