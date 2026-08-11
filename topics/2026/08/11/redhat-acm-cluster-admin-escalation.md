# Red Hat ACMの重大な脆弱性、名前空間編集権限のみでKubernetesクラスタ管理者に昇格可能
Tags: Security, Cloud

- Red Hat ACM Flaw Lets Namespace Editors Escalate to Full Kubernetes Cluster Admin (2026-08-05)
  https://cyberpress.org/red-hat-acm-flaw-namespace-editors-escalate/
- Red Hat ACM Privilege Escalation Vulnerability Lets Attackers Gain Full Cluster-Admin Access (2026-08-05)
  https://cybersecuritynews.com/red-hat-acm-privilege-escalation-vulnerability/
- Red Hat Kubernetes Flaw Allows Attackers to Escalate Privileges to Cluster-Admin (2026-08-05)
  https://gbhackers.com/red-hat-kubernetes-flaw/

Red Hat Advanced Cluster Management(ACM)にCVSS 9.9の重大な脆弱性(CVE-2026-10090)が発見された。名前空間レベルの編集権限しか持たないユーザーが、悪意あるHelmリポジトリを介してApplication Subscriptionコントローラーを悪用し、Kubernetesクラスタの完全な管理者権限まで昇格できることが判明した。
