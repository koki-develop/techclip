# AtlassianのAIエージェント「Rovo」に複数の情報漏洩脆弱性、JiraやConfluenceのデータが外部流出の恐れ
Tags: Security, AI

- Atlassian Rovo Can Be Tricked Into Sending Jira and Confluence Data to Attackers (2026-08-05)
  https://thehackernews.com/2026/08/atlassian-rovo-can-be-tricked-into.html
- PromptArmor: Atlassian Rovo Exfiltrates Data, Bypassing Controls (2026-08-05)
  https://www.promptarmor.com/resources/atlassian-rovo-exfiltrates-data
- SecurityWeek: Critical One-Click Vulnerability in Atlassian's Rovo AI Exposed Enterprise Data (2026-08-08)
  https://www.securityweek.com/critical-one-click-vulnerability-in-atlassians-rovo-ai-exposed-enterprise-data/

AtlassianのAIアシスタント「Rovo」に、間接的なプロンプトインジェクションを悪用してユーザーがアクセス可能なJiraやConfluenceのデータを外部の攻撃者サーバーへ送信させられる脆弱性が、PromptArmorとVaronis Threat Labsによりそれぞれ独立して発見された。Varonisが発見した「RovoBlast」と呼ばれるワンクリック型の脆弱性はDEF CONで公表され既に修正済みだが、PromptArmorが報告したゼロクリック型の間接プロンプトインジェクションは開示時点で未解決だったとされる。
