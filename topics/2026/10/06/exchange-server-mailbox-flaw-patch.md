# Microsoftが緊急パッチでExchange Serverの権限昇格の脆弱性(CVE-2026-96940)を修正、他ユーザーのメールが閲覧可能に
Tags: Security

- Out-of-band Exchange Server update fixes high-severity mailbox access bug (CVE-2026-96940) (2026-10-05)
  https://www.helpnetsecurity.com/2026/10/05/exchange-server-vulnerability-cve-2026-96940/
- Microsoft Exchange Flaw Lets Authenticated Attackers Read Other Users' Mailboxes (2026-10-05)
  https://thehackernews.com/2026/10/microsoft-exchange-flaw-lets.html
- Microsoft pushes Exchange update (2026-10-05)
  https://www.heise.de/en/news/Microsoft-pushes-Exchange-update-11475574.html

Microsoftはオンプレミス版Exchange Server(2016、2019、Subscription Edition)に存在する権限昇格の脆弱性CVE-2026-96940(CVSS 8.8)を修正する緊急のOut-of-band更新プログラムを公開した。認証済み攻撃者が同一組織内の他ユーザーのメールボックスや添付ファイルを不正に閲覧できる恐れがあり、発見したMicrosoftの研究者は「悪用される可能性が高い」と評価している。なお今回の更新には副作用があり、公開カレンダーでのHTTP 500エラーや韓国語処理でのデッドロックといった不具合も報告されており、追加の修正が予定されている。
