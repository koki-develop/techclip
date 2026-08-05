---
date: "2026-08-05T14:53:56+09:00"
title: "Google Password Manager同期パスキーを狙う「Pass-ta-key」攻撃、Unit 42が3つの手法を報告"
description: "Palo Alto Networks傘下のUnit 42が、Windows端末上のマルウェアがGoogle Password Managerの同期パスキーを、指紋やPIN認証を経ずに乗っ取れる「Pass-ta-key」攻撃群を報告した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/08/google-password-manager-attacks-could.html"
  - "https://www.bleepingcomputer.com/news/security/new-pass-ta-key-attacks-let-malware-hijack-google-synced-passkeys/"
  - "https://9to5google.com/2026/08/04/google-password-manager-passkeys-could-be-at-risk/"
---

## 概要

Palo Alto Networks傘下のセキュリティ研究チームUnit 42は、Windows上のChromeで動作するGoogle Password Managerの同期パスキー機能を狙う3種類の攻撃手法を発見し、公表した。総称して「Pass-ta-key」と呼ばれるこれらの攻撃は、パスキーの暗号技術そのものを破るものではなく、端末が既にマルウェアに感染していることを前提に、本来は指紋やPINによる本人確認（ユーザー検証）を経ずに、パスキーで保護されたアカウントへの不正ログインを可能にするというものだ。TPM（トラステッド・プラットフォーム・モジュール）を搭載したWindowsデバイスが対象で、クリーンな環境であれば影響を受けない。

## 3つの攻撃手法

最も基本的な「Pass-ta-key」は、Chromeが保持するTPMバックアップ用のデバイス識別キーを悪用し、Windows Cryptography APIを通じて有効な認証応答を作り出す手法で、管理者権限もユーザーの操作も不要とされる。ただし、返される「User Verified（UV）フラグ」を厳密に検証するサービスにはこの手法は通用しない。

第2の「Silver Pass-ta-key」は、被害者のデバイスを強制的に再登録させたうえで、攻撃者自身のユーザー検証キーを登録させる手法だ。クラウド側の認証器が新規登録キーの正当性（セキュアハードウェア由来かどうか)を検証していないという設計上の弱点を突くもので、ユーザー検証が必須に設定されたアカウントに対しても有効とされる。

最も深刻とされるのが第3の「Golden Pass-ta-key」で、Password Manager内の全パスキーを暗号化・復号する32バイトの「セキュリティドメインシークレット（SDS)」を、Chromeのプロセスメモリから直接ダンプして抽出する。このマスターキーを奪われると、同期された全パスキーの秘密鍵を復号できてしまうため、影響範囲が最も大きい。

## 発見・報告と対応

Unit 42はこれらの脆弱性をGoogleをはじめとする関係各社に責任開示のかたちで報告済みだ。実例としてGitHubはユーザー検証フラグを厳格に確認する実装になっていたため基本的な攻撃を防げた一方、eBayは検証が不十分だったため報告を受けて修正を行ったという。Googleはログから秘密鍵情報を削除する対応を行ったが、記事執筆時点でも鍵はChromeのプロセスメモリ上からアクセス可能な状態にあり、根本的な対策には至っていない。なお、現時点で実際の悪用（in the wild）は報告されておらず、CVE識別子も割り当てられていない。

## 今後の対策と展望

Unit 42は、リライング・パーティ（認証を利用するサービス側）に対し、userVerificationを必須に設定したうえで返されるUVビットを確実に検証することを推奨している。また認証プロバイダー側には、新規登録キーに対するハードウェア証明の要求、アクセス制御の強化、マスターキーのローテーションや失効機能の実装などが求められるとしている。パスキーは共有・盗み見・使い回しのリスクがない点で従来のパスワードより本質的に安全とされてきたが、今回の報告は、端末そのものがマルウェアに侵害された場合にはその優位性が薄れることを示すものであり、Google以外のパスキー実装にも同様のリスクが潜んでいる可能性が指摘されている。
