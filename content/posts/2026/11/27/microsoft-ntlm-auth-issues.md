---
date: "2026-11-27T08:07:42+09:00"
title: "Microsoft、NTLM署名強化を含む11月更新でサードパーティ製品の認証エラーを確認"
description: "MicrosoftはWindows RPCの脆弱性CVE-2026-118737に対処した11月のセキュリティ更新でNTLMメッセージ署名の強制を強化した結果、認証プロキシやSSO製品などサードパーティ製品でログイン失敗が発生していることを確認した。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/microsoft/microsoft-confirms-authentication-issues-after-november-updates/"
  - "https://www.theregister.com/security/2026/11/25/microsofts-ntlm-security-changes-trip-up-third-party-logins/5312085"
---

## 概要

Microsoftは11月のセキュリティ更新適用後、一部のサードパーティ製品で認証エラーが発生していることを確認した。今回の更新は、Windows RPC Runtimeに存在する深刻度の高いタイミング依存の脆弱性(CVE-2026-118737)に対処するもので、認証されていない攻撃者がユーザー操作なしでリモートコード実行を行えるという重大な欠陥を修正する内容だった。しかしこの修正と合わせてNTLMメッセージ署名の強制が強化されたことで、リレー攻撃対策が進む一方、プロトコルを厳密に実装していない一部のサードパーティ製品との互換性問題が表面化した。

## 原因と影響範囲

問題が生じているのは、認証プロキシサーバー、シングルサインオン(SSO)ソリューション、アプリケーションパッケージングツールなど、NTLMSSP_NEGOTIATE_TARGET_INFOフラグを設定しながらCHALLENGE_MESSAGE内のTargetInfoフィールドを空または不完全なまま送信している製品だ。これらはNTLM署名強制が強化される以前は問題なく動作していたが、Microsoftが署名検証を厳格化したことで認証に失敗するようになった。言い換えれば、不具合の根はMicrosoft側ではなくサードパーティ製品の実装の不完全さにあるが、今回の更新でその欠陥が顕在化した形だ。

## 回避策と今後の展開

Microsoftは恒久的な対応として各ベンダーによる更新の提供やKerberos認証への移行を推奨する一方、短期的な回避策としてレジストリキー`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa\MSV1_0`内の`ClientAllowUnsignedNtlm`を1に設定する方法を案内している。ただし同社はこれが暫定的な措置であり、将来的に削除される可能性があると強調しており、恒久的な解決策としては推奨していない。

NTLM署名の強制は段階的に展開されており、今回はその第1段階にあたる。2027年5月に予定されているフェーズ2では、Windowsサーバー側でNTLM署名が必須化され、署名に対応していないクライアントからの接続は拒否されるようになる見込みだ。管理者は手元の認証プロキシやSSO製品、パッケージングツールが今回の問題に該当しないか確認し、ベンダーの対応状況を踏まえて早めに移行計画を立てる必要がある。なお今月のセキュリティ更新では、インストール障害やSQL Serverのパフォーマンス低下、複雑な書式を含む印刷文書の破損といった別の不具合も報告されている。
