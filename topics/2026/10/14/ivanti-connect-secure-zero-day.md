# Ivanti Connect Secureの連鎖型ゼロデイ脆弱性が実悪用、完全パッチ済み機器でroot権限奪取
Tags: Security

- Ivanti warns of Connect Secure zero-day exploited in attacks (2026-10-13)
  https://www.bleepingcomputer.com/news/security/ivanti-warns-of-connect-secure-zero-day-exploited-in-attacks/
- Attacker Chains Three Ivanti Connect Secure Zero-Days for Root Access, Only Two Patched So Far (2026-10-13)
  https://thehackernews.com/2026/10/attacker-chains-three-ivanti-connect.html
- A Series of Unauthenticated Events: Chained Exploitation of Ivanti Connect Secure Zero-Days (2026-10-13)
  https://www.volexity.com/blog/2026/10/13/a-series-of-unauthenticated-events-chained-exploitation-of-ivanti-connect-secure-zero-days/

Ivanti Connect Secureのリモートアクセスゲートウェイにおいて、攻撃者グループ「UTA0576」が3件のゼロデイ脆弱性(CVE-2026-104935を含む)を連鎖的に悪用し、完全パッチ済みのシステムでも未認証のままroot権限を奪取していることが、脆弱性を発見したVolexity社の調査と複数の報道により明らかになった。攻撃は10月3日から継続しており、資格情報の窃取やActive Directoryへの侵入、ログ改ざんによる証拠隠滅などの手口が確認されている。Ivantiは3件のうち2件へのパッチを公開済みだが、権限昇格に使われる脆弱性は10月13日時点で未修正のままだと報じられている。
