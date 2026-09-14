# JFrog Artifactoryの脆弱性を連鎖悪用しバックドア設置、6週間経過後も6割弱が未対策
Tags: Security

- Artifactory flaws chained in attacks deploying backdoor malware (2026-09-11)
  https://www.bleepingcomputer.com/news/security/artifactory-flaws-chained-in-attacks-deploying-backdoor-malware/
- Artifactory Under Attack: In-the-Wild Exploitation of CVE-2026-42016, CVE-2026-42018 & CVE-2026-82329 (2026-09-10)
  https://www.wiz.io/blog/artifactory-under-attack-in-the-wild-exploitation-of-cve-2026-42016-cve-2026-4201
- Three JFrog Artifactory Flaws Exploited for Backdoor Deployment (2026-09-14)
  https://www.securityweek.com/three-jfrog-artifactory-flaws-exploited-for-backdoor-deployment/

攻撃者がJFrog Artifactoryの複数の脆弱性(CVE-2026-42018、CVE-2026-42016、CVE-2026-82329)を連鎖させ、匿名ユーザートークンの窃取からわずか5分以内で管理者権限を奪取する攻撃が確認された。Wiz Researchの調査によると、攻撃者は永続的な管理者アカウントの作成や悪意あるプラグインの導入によりRust製バックドアを展開し、クラスター内の機密データ抽出も行っていた。開示から6週間が経過した時点でも、インターネットに公開されているインスタンスの約59%がCVE-2026-42016に対して未対策のままであり、CISAはこれらの脆弱性を既知の悪用脆弱性(KEV)カタログに追加して連邦機関に2週間以内のパッチ適用を義務付けた。
