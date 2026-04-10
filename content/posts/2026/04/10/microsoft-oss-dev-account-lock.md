---
date: "2026-04-10T18:25:29+09:00"
title: "MicrosoftがWireGuard・VeraCrypt等の開発者アカウントを突然停止、セキュリティパッチ配布が不能に"
description: "MicrosoftがWireGuard・VeraCrypt・WindscribeなどのOSS開発者のWindows Hardware Programアカウントを予告なく停止し、Windowsドライバーの署名・更新配布が一時不能となった。"
tags:
  - OSS
  - Security
references:
  - "https://techcrunch.com/2026/04/08/wireguard-vpn-developer-cant-ship-software-updates-after-microsoft-locks-account/"
  - "https://techcrunch.com/2026/04/08/veracrypt-encryption-software-windows-microsoft-lock-boot-issues/"
  - "https://www.theregister.com/2026/04/09/microsoft_dev_account_deactivations/"
  - "https://www.techradar.com/vpn/vpn-privacy-security/microsofts-baffling-account-ban-blocks-security-patches-for-windscribe-wireguard-vpn-veracrypt"
---

## 何が起きたか

2026年3月末から4月初頭にかけて、WireGuard VPNの作者Jason DonenfeldやVeraCryptの作者Mounir Idrassiなど、広く使われているセキュリティ系オープンソースソフトウェアの開発者たちが、MicrosoftのWindows Hardware Programのアカウントを事前警告・説明なしに突然停止させられた。この停止により、WireGuard・VeraCrypt・Windscribe VPNといったプロジェクトがWindowsドライバーの署名や更新の配布を行えない状態に陥った。

DonenfeldとIdrassiはいずれも「Microsoftからメールも事前警告も一切届かなかった」と証言している。ある日サインインしようとしたらアカウントが停止されており、何の説明も受けていないという状況だった。

## セキュリティへの深刻なリスク

今回の停止は単なる利便性の問題にとどまらず、ユーザーへの直接的なセキュリティリスクをもたらした。Donenfeldは「もしWireGuardにゼロデイ脆弱性が発見されても、今の状態ではセキュリティパッチを出せない。今こそゼロデイを悪用し始めるのに絶好のタイミングだ」と警鐘を鳴らした。

VeraCryptについてはより深刻な問題も指摘された。VeraCryptはディスク全体を暗号化するソフトウェアであり、Windowsの起動プロセスに深く関わっている。開発者がアップデートを配布できないまま放置された場合、2026年7月以降にVeraCryptを使用しているWindowsデバイスで起動障害が発生する可能性があるという。

## Microsoftの主張と欠陥のある通知プロセス

MicrosoftはWindows Hardware Programにおけるアカウント認証（verification）の義務化を2025年10月のブログ投稿で発表しており、同社は「2週間の猶予期間中にメール・バナー・リマインダーを送った」と主張している。しかし実際には開発者への通知が届いておらず、通知プロセスの欠陥が明らかとなった。

さらに問題だったのは、停止後の対応手段がほぼ存在しなかった点だ。停止されたアカウントからは異議申し立てシステムにアクセスできない設計になっており、AIサポートツールも適切な担当窓口を特定できなかった。審査キューは60日待ちの状態で、迅速対応の手段がなかった。

## 公開告発を受けてMicrosoftが謝罪・復旧を約束

開発者がSNSやメディアを通じて問題を公開告発すると、MicrosoftのプレジデントPavan Davuluri氏がSNSで問題を認め、「近日中にアカウントを復旧する」と約束した。通知プロセスの改善についても約束され、WireGuardのアカウントは2026年4月10日に復旧が確認された。

今回の一連の騒動は、大手プラットフォームによるOSSエコシステムへの依存と、その管理・通知プロセスの脆弱性を改めて露呈させた形となった。セキュリティ系ソフトウェアの開発者アカウントが突然停止されるリスクは、エンドユーザーのセキュリティに直結する問題として、今後のプラットフォームポリシーのあり方が問われている。
