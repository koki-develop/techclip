# macOSの画面共有機能に認証前RCE脆弱性、インターネット公開端末を狙いMoneroマイナーを設置する攻撃が発覚
Tags: Security

- Hackers exploit macOS Screen Sharing flaw to deploy Monero miner (2026-08-14)
  https://www.bleepingcomputer.com/news/security/hackers-exploit-macos-screen-sharing-flaw-to-deploy-monero-miner/
- MacOS screen sharing vulnerability actively exploited for crypto mining (2026-08-14)
  https://www.scworld.com/brief/macos-screen-sharing-vulnerability-actively-exploited-for-crypto-mining

macOSの画面共有機能(Screen Sharing)のSRP実装に存在する認証前リモートコード実行の脆弱性(CVE-2026-65400)が悪用され、ポート5900をインターネットに公開しているMacにroot権限で侵入しMoneroマイナーを設置する攻撃が確認された。Appleは8月6日付で修正済みだが、専門家は未適用の端末に対し画面共有の無効化やポートの非公開化を推奨している。
