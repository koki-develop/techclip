---
date: "2026-07-01T02:40:55+09:00"
title: "Linux FoundationがAI脅威に対抗するOSSセキュリティ組織「Akrites」を設立——大手テック・金融20社が結集"
description: "Linux FoundationがAIによる脆弱性発見・悪用の加速に対応するため、AWS・Anthropic・Google・Microsoft・OpenAIなど約20組織が参加するオープンソースセキュリティ組織「Akrites」を設立した。"
tags:
  - OSS
  - Security
references:
  - "https://www.linuxfoundation.org/press/linux-foundation-and-industry-leaders-launch-akrites-to-defend-critical-open-source-software-against-ai-enabled-cyber-threats"
  - "https://www.helpnetsecurity.com/2026/06/26/akrites-open-source-security-framework/"
  - "https://thenewstack.io/akrites-open-source-vulnerability-coordination/"
---

## 概要

Linux Foundationは2026年6月25日、AI時代のサイバー脅威から重要なオープンソースソフトウェア（OSS）を守るための業界横断組織「Akrites」の設立を発表した。Amazon Web Services、Anthropic、Cisco、Citi、Ericsson、GitHub、Google、IBM、JPMorgan Chase、Microsoft、NVIDIA、OpenAI、Red Hat、Rust Foundation、Sonatype、Vodafone、Zscalerなど約20の企業・団体が創立メンバーとして参加しており、テクノロジー企業にとどまらず金融機関や通信キャリアも名を連ねる。初期資金はAlpha-Omegaが提供し、追加参加はakrites.orgで受け付けている。

設立の直接的な契機のひとつは、AI基盤モデルの利用をめぐるセキュリティ懸念の高まりとされる。The New Stackの報道によると、Anthropicとほかの19組織が連名でこの取り組みを始動させた背景には、最先端AIモデルが脆弱性探索に転用されるリスクへの危機感がある。こうした問題意識を受け、業界として統一した脆弱性対応の枠組みを構築する必要性が共有された。

## AI時代の脅威環境と設立の背景

従来、ゼロデイ脆弱性の発見には高度な専門知識を持つセキュリティ研究者が数週間を費やすことが一般的だった。しかし現在のフロンティアAIモデルは、同等の作業を数分で実行できるまでになっている。OSS は銀行・医療・エネルギー・政府システムなど世界の重要インフラを広く支えているにもかかわらず、多くのプロジェクトは小規模なボランティアチームによって保守されており、AI支援による攻撃の急増に単独で対応する体力を持たない。Akritesはこのギャップを埋める「業界共通の防衛ラインと最後の砦」として機能することを目指している。

## 技術的な枠組み：共有SIRT と標準化されたCVDプロセス

Akritesの中核は二つの仕組みで構成される。第一は**共有セキュリティインシデント対応チーム（SIRT）**で、加盟組織が人的リソースと知見を持ち寄り、重大な脆弱性の修復を協調して支援する。第二は**標準化された脆弱性協調開示（CVD）プロセス**で、脆弱性の報告受付から修正適用・公開開示までの共通ワークフローと業界標準ツールを整備する。

修正パッチは基本的に元のプロジェクトに戻され、メンテナの管理下で適用される。ただしメンテナが不活発なパッケージについては、Akritesが直接対応の「最後の砦」となる運用が想定されている。金融・医療・電気通信・エネルギー・政府・AIインフラなど幅広いセクターで使われるOSSプロジェクトが対象となり、特定のエコシステムに偏らない水平的なセキュリティ支援を提供する。

## 今後の展望

Akritesは設立直後から幅広い産業セクターにまたがる参加組織を確保しており、業界主導のOSSセキュリティ基盤として実効性のある運営が期待される。AIによる脆弱性発見の民主化が進む中、個々のプロジェクトや企業が孤立した対応を続けることの限界は明白であり、Akritesのような業界横断の調整機関の需要は今後さらに高まると見られる。追加の参加組織の募集が続いており、エコシステムの拡大とともに対応できる脆弱性の範囲と速度が向上していくことが見込まれる。
