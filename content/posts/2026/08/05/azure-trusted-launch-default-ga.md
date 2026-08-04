---
date: "2026-08-05T08:20:08+09:00"
title: "Azure、新規Gen2 VMでセキュアブートとvTPMを既定で有効化する「Trusted Launch as Default」が正式提供"
description: "AzureはGen2仮想マシンおよびスケールセットの新規デプロイでセキュアブートとvTPMを追加コストなしで標準有効化する「Trusted Launch as Default」を正式提供開始した。"
tags:
  - Cloud
  - Security
references:
  - "https://techcommunity.microsoft.com/blog/microsoft-security-blog/secure-by-default-trusted-launch-as-default-is-now-generally-available/4541672"
---

## 概要

Microsoftは8月3日、Azureの新規Gen2仮想マシン（VM）およびスケールセットに対してセキュアブートと仮想TPM（vTPM）を標準で有効化する「Trusted Launch as Default（TLaD）」を正式提供開始（GA）したと発表した。ARMテンプレート、Bicep、Terraformなどどのクライアントツール経由でデプロイした場合でも、対象となる新規Gen2 VM・スケールセットはTrusted Launch構成でセキュアブートとvTPMが有効な状態で作成されるようになる。追加コストは発生せず、デプロイコード側で明示的な指定がない限りこの既定値が上書きされることもない。なお、AzureポータルやCLI、PowerShell経由の作成では、この機能のプレビュー登録の有無にかかわらず、以前からTrusted Launchが既定で有効になっている。

## 技術的な詳細

Trusted Launchはブートキットやルートキット、低レイヤーのマルウェア攻撃に対する防御を強化するための複数の協調したインフラ技術で構成される。中核となるセキュアブートはプラットフォームファーム上で実装され、信頼された発行元が署名したブートローダー・OSカーネル・ドライバのみを起動対象とすることで、ソフトウェアスタックの「信頼の起点（root of trust）」を確立する。署名の検証に失敗した場合、VMは起動しない。もう一方の柱であるvTPMはTPM 2.0仕様に準拠した仮想化TPMで、VMからは独立したセキュアな環境で動作し、鍵や測定値を保管する専用の金庫として機能する。vTPMはUEFI・OS・システム・ドライバに至るブートチェーン全体を測定し、リモートアテステーションを通じてMicrosoft Defender for Cloudと連携する。アテステーションに失敗した場合はブート整合性の問題を示す統合性アラートが発行される仕組みだ。対応VMサイズはB・D・E・F・L・NC/ND/NVファミリーなどx64およびArm64（Cobalt 100ベース）の主要シリーズに及び、すべてのパブリックリージョン、Azure Government、Azure Chinaリージョンで利用できる。

## 有効化の仕組みと注意点

Azureポータル・CLI・PowerShellでは従来どおり常にTrusted Launchが既定となる一方、ARMテンプレートやBicep、Terraformなど別のクライアントツール経由でTLaDを利用するには、サブスクリプション上でMicrosoft.Compute名前空間のプレビュー機能「TrustedLaunchByDefaultPreview」を登録する必要がある。API version 2025-11-01以降を使うと、Marketplaceイメージ・Azure Compute GalleryイメージがTrusted Launch対応であること、ディスクとVMサイズがTrusted Launchをサポートしていることなど一定の条件を満たす場合に自動的にTrusted Launchが適用される。条件を満たさない場合はエラーにはならず、Trusted Launchなしで通常どおりVMが作成される。既定を明示的にバイパスしたい場合は`securityType`パラメータを`Standard`に設定すればよい。また、既存のVMやスケールセットはTLaDの影響を受けず、この変更が適用されるのは新規デプロイのみである。なお既知の制限として、いったんTrusted Launchで作成したVMをM-seriesなど非対応のVMサイズファミリーへリサイズすることはできず、必要な場合はVMを割り当て解除したうえでAPI経由で`securityType`を`Standard`に変更する対応が求められる。

## 背景と今後の展望

Trusted Launch自体は既存の機能だが、これまでは利用者が明示的に有効化する必要があった。今回のGAにより、新規デプロイ時点でのセキュリティベースラインが自動的に底上げされ、意図せずセキュアブートやvTPMが無効なまま本番稼働するVMが減ることが期待される。Microsoft Defender for Cloudは従来からセキュアブートやvTPMが無効なVMに対して低重要度の推奨事項を出しているが、TLaDによって新規VMではそもそもこうした推奨事項が発生しにくくなる。既存VMについては別途「Enable Trusted launch on existing Gen2 VMs」などの手順に沿った移行が必要であり、既存フリートを含めた全面的な底上げには利用者側の対応が引き続き求められる点には留意したい。
