---
date: "2026-10-02T08:11:12+09:00"
title: "ZimbraのSNMP機能に未認証コマンドインジェクション、Webシェル設置から認証情報窃取まで多段階攻撃が進行中"
description: "ZimbraのSNMP通知機能に存在する未認証コマンドインジェクション脆弱性CVE-2026-73570が実悪用され、攻撃者がWebシェル設置・権限昇格・認証情報窃取に至る多段階攻撃を展開していることがMicrosoftの調査で判明した。"
tags:
  - Security
references:
  - "https://thehackernews.com/2026/09/attackers-exploit-zimbra-flaw-to-deploy.html"
  - "https://www.microsoft.com/en-us/security/blog/2026/09/30/unauthenticated-command-injection-on-internet-facing-mail-servers-tracking-cve-2026-73570/"
---

## 概要

Zimbra Collaboration Suite(ZCS)のSNMP通知機能に存在する未認証コマンドインジェクションの脆弱性(CVE-2026-73570、CVSSスコア8.9)が実際に悪用されていることが、Microsoft Threat Intelligenceの調査で明らかになった。オプションパッケージの`zimbra-snmp`がインストールされ、かつSNMP通知が有効なインターネット公開メールサーバーが標的となっており、攻撃者は特殊に細工したSMTPリクエストを送信するだけで、ユーザー操作なしにzimbraサービスアカウント権限でリモートコード実行を達成できる。Microsoftによれば、侵害を受けた環境ではJSP形式のWebシェルやリバースシェルの展開、権限昇格、永続的なリモートアクセスツールの設置、メモリ上での実行など、一連の高度な攻撃チェーンが観測されている。脆弱性の修正版である10.1.20は2026年7月20日に公開済みだが、Microsoftによれば同日から8月13日の脆弱性公開までの間に未パッチのサーバーへの攻撃活動が確認されている。

## 脆弱性の仕組みと悪用条件

この脆弱性は、SNMP通知処理が信頼できない入力を適切にサニタイズしないことに起因する。攻撃者はSMTPリクエストにシェルメタキャラクターを埋め込み、`swatchdog`や`snmptrap`の実行パスを経由することで、認証なしにOSコマンドを注入できる。悪用には「zimbra-snmpパッケージの導入」と「SNMP通知の有効化」という2条件が必要だが、これらはオプション機能であるため、全てのZimbra導入環境が対象になるわけではない。しかし条件を満たすサーバーはインターネットから直接到達可能なケースが多く、実際の攻撃では複数のOOB(out-of-band)スキャンツールを用いた偵察・プローブ活動が2026年7月28日から8月7日にかけて確認されており、HTTP・DNS・ICMPのコールバックを使った外部コラボレーターサービス(oast.fun、oast.onlineなど)経由でコマンド実行の成否を検証する手口が使われていた。

## 多段階の攻撃チェーン

Microsoftが観測した攻撃は、偵察から情報窃取まで複数の段階を経る組織的なキャンペーンの様相を呈している。初期侵入後、攻撃者はJettyのアプリケーションディレクトリやmailboxdのサーブレット作業ディレクトリにJSP形式のWebシェルを設置し、クラスタを構成する他のメールボックスノードにも複製した。続く権限昇格の段階では、Zimbraの正規のsudo許可ヘルパー(`zmmailboxdmgr`など)や書き込み可能なログディレクトリ、PAM設定の操作(`pam_exec`経由)、`zmstat-fd`ヘルパーを悪用してroot権限を取得し、sudoersに「NOPASSWD: ALL」のエントリを追加してパスワードなしのsudo実行を可能にしていた。永続化にはsystemdサービス(正規サービスを装ったタイムスタンプ偽装を含む)、OpenRC、cron、SSHの`authorized_keys`、さらに`memfd_create`を用いたメモリ上での実行など、複数の手法が並行して使われていた。

## 認証情報窃取とデータ流出

攻撃者は`zmlocalconfig -s`や認証済みの`ldapsearch`を駆使し、LDAP・MySQL・Postfix・Amavis向けのZimbraサービス認証情報に加え、アカウント認証に使う`zimbraPreAuthKey`、セッショントークン署名鍵の`zimbraAuthTokenKey`、`zimbraTwoFactorAuthSecret`といった極めて機微な秘密情報を収集した。さらに`mailbox`、`mailbox_metadata`、`mobile_devices`、`out_of_office`といったデータベーステーブルをエクスポートし、メールボックス全体のバックアップやSSL証明書・秘密鍵も窃取対象となった。攻撃キットには軽量ダウンローダーの`agent2.sh`、Go言語製インストーラーの`zimdown2`、対話型シェルやファイル操作、SOCKS5プロキシ機能を備えたフル機能RATの`zimclient2`、Zimbra特化の窃取ツール`zimbra-exfil`が含まれ、C2通信にはHTTP/HTTPS、DNSラベル、OpenSSLベースの暗号化リバースシェルなど複数のチャネルが使われた。窃取したデータをAzure Blobストレージへ転送しようとする試みも確認されている。

## 対策と今後の展望

本脆弱性は既にCISAのKnown Exploited Vulnerabilities(KEV)カタログに登録され、連邦機関には2026年8月24日までの対応が義務付けられた。Microsoftは、Zimbraを10.1.20以降へ直ちにアップグレードすることを最優先の対策として推奨し、やむを得ず旧バージョンを使い続ける場合は`zimbra-snmp`パッケージのアンインストール、SNMP通知の無効化、SNMP/SMTPアクセスの信頼できるホストへの制限を求めている。既に侵害が疑われる環境では、`zimbraPreAuthKey`をはじめとする全ての認証シークレットのローテーション、systemdユニットやPAM設定・sudoersの異常検査、複数のZimbraノードにまたがるJSPウェブシェルの捜索が不可欠だとしている。Microsoft Defenderは本攻撃パターンに対応する検出シグネチャ(「Exploit:Linux/SnmpTrapCmdInject.A」や「HackTool:Linux/ZimbraPLE.A」など)や7種類のAdvanced Huntingクエリを提供しており、署名一致だけに頼らず振る舞いベースの調査を組み合わせることが、同種の侵害の早期発見につながるとみられる。
