---
date: "2026-04-13T02:16:50+09:00"
title: "Chrome 146でDBSC一般提供開始、TPMを活用してセッションCookie窃取を無効化"
description: "GoogleがChrome 146でDevice Bound Session Credentials（DBSC）をWindows向けに一般公開し、インフォスティーラーによるセッションCookie窃取攻撃への対策を強化した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/04/google-rolls-out-dbsc-in-chrome-146-to.html"
  - "https://www.bleepingcomputer.com/news/security/google-chrome-adds-infostealer-protection-against-session-cookie-theft/"
  - "https://www.helpnetsecurity.com/2026/04/10/google-chrome-device-bound-session-credentials/"
---

## 概要

Googleは2026年4月、Chrome 146のすべてのWindowsユーザーを対象にDevice Bound Session Credentials（DBSC）を一般提供開始した。DBSCはセッションをデバイスのハードウェアに暗号的に紐付ける技術で、LummaやVidar、Atomicといったインフォスティーラーマルウェアが悪用するセッションCookie窃取攻撃を根本から無効化することを目的としている。macOSへの対応は今後のChromeリリースで予定されている。

## 仕組みと技術的詳細

DBSCはWindows上のTPM（Trusted Platform Module）やmacOS上のSecure Enclaveといったハードウェアセキュリティモジュールを活用し、デバイスごとに固有の公開鍵・秘密鍵ペアを生成する。この秘密鍵はデバイスの外部にエクスポートできないよう設計されており、サーバーがセッション中に短命なCookieを発行する際、ブラウザは対応する秘密鍵の所持を暗号学的に証明しなければならない。その結果、たとえ攻撃者がローカルストレージからCookieを盗み出したとしても、秘密鍵なしには更新できないため、窃取されたCookieはほぼ即座に無効化される。各セッションは独立した暗号鍵を使用するため、クロスサイト追跡やデバイスフィンガープリントのリスクも排除されており、デバイス識別子がサーバーへ送信されることもない。ハードウェアが対応していない環境では、自動的に標準動作へフォールバックする設計になっている。

## 実績と業界連携

Googleは過去1年間、OktaなどのパートナーとDBSCのテストを進めており、セッション窃取イベントの顕著な減少が観測されたと報告している。また、本技術はMicrosoftとの共同設計によるオープンなWeb標準として開発され、W3CのWeb Application Security Working Groupにも採用されている。バックエンドへの導入には専用の登録エンドポイントと更新エンドポイントの実装が必要だが、既存のフロントエンドとの互換性は維持されており、実装ガイダンスはChrome Developerポータルおよび仕様として参照できる。

## 今後の展望

現時点ではWindows版Chrome 146への展開が完了しており、macOS対応が次のマイルストーンとなる。DBSCはセッションハイジャック攻撃に対する業界横断的な標準防御レイヤーとして位置づけられており、他のブラウザベンダーや認証プロバイダーへの普及が進めば、Cookie窃取を前提とした攻撃手法の実効性を大幅に低下させる可能性がある。
