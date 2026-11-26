# Microsoft、11月セキュリティ更新のNTLM署名強化でサードパーティ製品の認証エラーが発生していることを確認
Tags: Security

- Microsoft confirms authentication issues after November updates (2026-11-25)
  https://www.bleepingcomputer.com/news/microsoft/microsoft-confirms-authentication-issues-after-november-updates/
- Microsoft's NTLM security changes trip up third-party logins (2026-11-25)
  https://www.theregister.com/security/2026/11/25/microsofts-ntlm-security-changes-trip-up-third-party-logins/5312085

Windows RPCのリモートコード実行脆弱性(CVE-2026-118737)に対処した11月のセキュリティ更新で、NTLMメッセージ署名の強制が強化されたことにより、認証プロキシやSSO製品、アプリパッケージングツールなど一部のサードパーティ製品でログイン失敗が発生していることをMicrosoftが確認した。原因は対象デバイスがCHALLENGE_MESSAGE内のTargetInfoフィールドを空または不完全なまま送信することで、Microsoftはレジストリ設定の調整やKerberos認証への切り替えといった回避策を案内している。NTLM署名強制は段階展開中で、フェーズ2は2027年5月に予定されている。
