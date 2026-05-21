---
date: "2026-05-22T02:43:51+09:00"
title: "SonicWall Gen6 VPNのMFA回避脆弱性CVE-2024-12802、不完全パッチ適用でランサムウェア攻撃に悪用"
description: "SonicWall Gen6 SSL-VPNのCVE-2024-12802に対するファームウェアパッチのみの適用ではMFA回避が残存し、2026年2〜3月にかけて複数組織での侵害が確認され、ランサムウェアグループAkiraと類似した活動パターンが観測された。"
tags:
  - Security
references:
  - "https://www.bleepingcomputer.com/news/security/hackers-bypass-sonicwall-vpn-mfa-due-to-incomplete-patching/"
  - "https://securityaffairs.com/192477/hacking/attackers-are-bypassing-mfa-on-sonicwall-vpns-because-something-was-wrong-with-previous-fix.html"
  - "https://www.cybersecuritydive.com/news/patch-bypass-hackers-exploit-flaw-sonicwall/820600/"
---

## 概要

SonicWall Gen6 SSL-VPNアプライアンスに存在する認証バイパス脆弱性 **CVE-2024-12802** を悪用した攻撃が、2026年2月〜3月にかけて複数組織で確認された。この脆弱性はSonicWallが2025年中に公開したファームウェアアップデートで修正済みとされていたが、Gen6デバイスではパッチ適用後もLDAPの手動再設定が必要であり、この追加手順を省略した環境でMFA（多要素認証）回避が引き続き可能な状態となっていた。SonicWallはアドバイザリを更新して手順の不備を告知しているが、攻撃者はすでにこの隙間を突いてランサムウェア展開を進めていた。

## 技術的な詳細

CVE-2024-12802 の根本原因は、SonicWallがMicrosoft Active DirectoryのログインフォーマットをUPN（User Principal Name、メール形式）とSAM（Security Account Manager、レガシー形式）で独立して処理する実装にある。MFAの強制はユーザーID単位ではなく各フォーマット単位で適用されるため、MFAがSAM経由のログインに設定されていても、UPN経由での認証を試みることで MFA をスキップできる。この問題はファームウェア更新だけでは解消されず、LDAP設定内のuserPrincipalName参照を削除・再設定するという6つの追加手順が必要である。手順には「既存のLDAP設定削除」「キャッシュされたLDAPユーザーの削除」「SSL VPNのUser Domain設定削除」「再起動後のLDAP再設定（UPN不使用）」「新規バックアップ作成」などが含まれる。通常のパッチ適用ワークフローではこれらの手動ステップが省かれやすく、管理者が修正済みと誤認したまま脆弱な状態が維持される点が問題視されている。なお、Gen7・Gen8デバイスはファームウェア更新のみで完全に修正される。

## 攻撃の手口と影響

攻撃者はまず自動化ツールを使ってVPN認証情報をブルートフォース攻撃し（場合によっては13回程度の試行で成功）、UPNログイン経路でMFAを回避してネットワークに侵入した。侵入後30〜60分以内に偵察、内部での認証情報の再利用テスト、Cobalt Strikeビーコンの展開、BYOVD（脆弱なドライバーの悪用）によるEDR回避ツールの設置が確認されている。攻撃者グループはランサムウェアグループ「Akira」と関連しており、初期アクセスブローカーとして侵害済み環境の売買も行っていたとみられる。CISAはこの脆弱性のCVSSスコアを9.1（Critical）と評価しており、SonicWall自身のスコア6.5を大きく上回る深刻度として位置づけている。

## 推奨される対策

Gen6デバイスを運用している組織は、ファームウェアを最新版に更新するだけでなく、SonicWallの公開アドバイザリに記載された6つの手動手順をすべて完了することが必須である。また、Gen6ハードウェアは2026年4月16日にサポート終了（End of Life）を迎えており、今後の脆弱性対応パッチの提供は見込めないため、Gen7またはGen8への移行が強く推奨される。侵害の痕跡を調査する際は、VPNログ内の `sess='CLI'` の記録、イベントID 238・1080を重点的に確認するとよい。
