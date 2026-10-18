---
date: "2026-10-19T08:09:49+09:00"
title: "NVIDIA、次世代ラック設計「Vera Rubin」をOCPにオープン化、AI工場のボトルネックは電力と施設へ"
description: "NVIDIAがOCPグローバルサミットでVera Rubinのラック・電源・ネットワーク設計を公開し、Cisco・Google・Meta・Microsoftらと共にAI工場インフラの業界標準化を推進している。"
tags:
  - AI
  - Cloud
references:
  - "https://blogs.nvidia.com/blog/ocp-global-summit-vera-rubin-scale-ai-factories/"
  - "https://www.storagenewsletter.com/2026/10/14/ocp-global-summit-2026-amid-ecosystem-adoption-nvidia-opens-vera-rubin-architecture-to-help-scale-ai-factories-worldwide/"
  - "https://convergedigest.com/nvidia-ocp-2026-vera-rubin-mgx-spectrum6-usfp/"
---

## 概要

NVIDIAはOpen Compute Project(OCP)グローバルサミットにおいて、次世代AIインフラ「Vera Rubin」のラックおよびコンピュートトレイ設計をMGXオープンアーキテクチャを通じてOCPに提供すると発表した。背景にあるのは、AI工場の拡張を阻む要因がGPUの供給制約から電力・冷却・施設建設へと移行しているという認識だ。NVIDIA副社長のIan Buck氏は、オープンインフラをAI工場の世界規模スケーリングにおける「不可欠な要素」と位置づけており、Cisco・Google・Meta・Microsoft・Visionbayといった主要企業がエコシステムパートナーとしてすでに採用を進めている。

## オープン化された技術仕様

今回更新されたMGX 1.2仕様には、ラック規模でのブラインドメイト液冷、ファンレス液冷コンピュートトレイ、5,000A対応の液冷バスバー、19インチ機器のネイティブサポートが含まれ、ラック当たり最大250kWの電力密度に対応する。電源面では800V DCアーキテクチャを採用し、従来の低電圧配電に伴う変換損失や配線の複雑さを軽減する設計となっている。ネットワークでは、Meta社が採用するSpectrum-6スイッチ(102.4Tb/s)がSpectrum-X Multiplane技術により最大8つのネットワーク平面にGPUトラフィックを分散し、10万GPU超級のファブリックに対応する。また、NVIDIAとCiscoが共同提案するUSFP光トランシーバ規格は、従来の200G/レーンOSFPモジュールと同等サイズで400Gb/レーンを実現し、16レーン構成から将来的に32レーンへの拡張も見込む。さらに「Vera CPU」ラック設計仕様は、ツール呼び出しや実行管理を支援するエージェント型AIワークロードに特化した構成となっている。

## エコシステムの参加企業とそれぞれの役割

Cisco・Google・Meta・Microsoft・Visionbayの5社は、それぞれ異なる形でVera Rubinアーキテクチャの実装に関わっている。MetaはSpectrum-6ベースのスイッチ「N-IceCube」を開発しFBOSSに統合、Multiplane技術の実運用検証を進めている。GoogleはFalcon Transport技術の実装を進めるほか、後述のグリッド復旧仕様の策定にも加わった。Microsoftも同仕様の策定に参画している。CiscoはUSFP光学トランシーバ標準の共同開発を担当する。VisionbayはNVIDIAの800V DC参照設計とVertiv社の電力・冷却技術を組み合わせた「K-1」プラットフォームを発表し、クラスタレベルの電力センターでAC-DC変換を一元化し高電圧DCをコンピューティングリソースの近傍まで引き込む構成を実現した。NVIDIAはこれに加え、ネットワーク設定自動化の「Config Manager」、クラスタ検証の「Cluster Readiness Engine」、ラックハードウェア抽象化の「Rack Management Service」、ベアメタル配備の「Cluster API Provider」という4種のオープンソースソフトウェアコンポーネントもDSX AI Factory向けに公開している。

## 背景と今後の見通し

AI工場の規模がメガワットからギガワットへと拡大する中、NVIDIAはAMD・Google・Metaと共同で施設設計を電源からラックレイアウトまで定義する「Open Data Center Specification v0.7」を策定したほか、Google・Meta・Microsoftと共に、グリッド障害から2秒以内の復旧を目指す「OCP Grid Resilience Specification」も発表した。業界分析では、ラック設計のオープン化によってFoxconn、Quanta、Wiwynn、Supermicroといったシステムビルダーが互換ラックの開発を迅速化できると指摘されている。今後は800V DC電源標準の段階的な普及に加え、EthernetがInfiniBandに対する優位性を広げる展開が見込まれるほか、DDNやVast Dataなどによるストレージ統合競争の激化も予想される。一方で、AMDの「Helios」ラックとの互換性がエコシステムの多様性を左右する要素になるとの見方も示されており、複数のラック規格が並立する中でどこまで標準化が進むかが今後の焦点となる。
