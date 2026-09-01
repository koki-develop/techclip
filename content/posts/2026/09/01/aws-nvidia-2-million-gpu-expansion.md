---
date: "2026-09-01T18:15:37+09:00"
title: "AWSとNvidia、提携を大幅拡大——2027〜2028年に追加200万基のGPU投入へ"
description: "AWSとNvidiaが戦略的提携を拡大し、2027〜2028年にBlackwell UltraやRubinなど追加200万基のGPUと次世代Vera CPU基盤インフラを投入すると発表した。"
tags:
  - Cloud
  - Other
references:
  - "https://nvidianews.nvidia.com/news/aws-and-nvidia-to-deliver-2-million-additional-gpus-and-next-generation-infrastructure-for-agentic-and-physical-ai"
  - "https://techcrunch.com/2026/08/26/amazon-just-tripled-its-order-of-nvidia-chips-over-surging-demand/"
  - "https://www.aboutamazon.com/news/aws/aws-nvidia-2-million-gpus-ai"
---

## 概要

AWSとNvidiaは8月26日、戦略的提携を大幅に拡大し、2027〜2028年にかけてBlackwell Ultra、Rubin、Rubin UltraのGPUを追加で200万基投入すると発表した。これは今年3月にNvidia GTC 2026で表明した100万基超のコミットメントからわずか5カ月で3倍近くに積み増した形で、Nvidiaは「需要が想定を上回っている」ことが背景にあるとしている。両社の協業は16年におよび、今回はGPU供給だけでなく、ネットワーク機器、ソフトウェアプラットフォーム、ロボティクススタックまで対象を広げた「フルスタック」の提携へと発展した。

## 技術的な詳細

今回の拡大には、NvidiaのVera CPUベースのシステムがAWS基盤に導入されることが含まれる。Vera CPUはエージェント型AIワークロードに求められるコード実行、ツール呼び出し、サンドボックス処理、解析といった高性能な処理を担う。またAWS独自のTrainiumチップはNvidiaのNVLink Fusion高速インターコネクトに対応し、カスタム高帯域幅メモリ(NVHBM)へのアクセスを可能にすることで、性能と電力効率の向上を図る。ネットワーク面ではNvidia Spectrumによる大規模AIトレーニング向けの最適化も進める。

GPU展開のうち10万基は、Impact Level 6以上に対応する米政府向けの機密ワークライン基盤に充てられる。既存インフラでの実績として、Amazon EMR上のApache Spark処理はGPUアクセラレーションにより従来のCPU構成比で最大3.7倍の処理速度と30%のコスト効率向上を実現しており、Amazon OpenSearch Serviceのベクトルインデックス作成も最大9倍の高速化かつ4分の1のコストで行えるという。EC2 G7インスタンスにはRTX PRO 4500 Blackwell Server Editionが採用され、前世代のG6比でAI推論性能4.6倍、グラフィックス性能2.1倍を実現するとしている。

## 背景と戦略的な意味合い

AWSのマット・ガーマンCEOは「顧客はAIワークロードに最適なツールを自由に選びたいと考えており、それらがシームレスに連携する確信も求めている」とコメント。Nvidiaのジェンスン・フアンCEOは「NvidiaとAWSはAI時代を代表する成長エンジンの一つを16年かけて築いてきた。需要はあらゆる予測を上回るペースで伸びている」と述べ、AIが「生産的で実用的な仕事をこなす段階に入った」ことが投資加速の背景にあると強調した。

興味深いのは、Amazonが自社製AIチップのTrainiumやGravitonを開発し、カスタムチップ事業だけで年換算250億ドル超の収益を上げながら、同時にNvidiaへの発注を大幅に積み増している点だ。これは特定ベンダーへの依存を避けつつ、爆発的に拡大するAIインフラ需要を取り込もうとする両面戦略の表れといえる。契約金額は非公開だが、アナリストは数百億ドル規模と推計している。Nvidia側もQ2売上高962億ドル(データセンター部門は前年比117%増の890億ドル)を記録し、Q3は1080億ドルへの拡大を見込むほか、2028会計年度までの製造能力確保に2790億ドルを投じると表明しており、AI関連投資の勢いは当面続く見通しだ。

今回の提携拡大は、AWSをNvidia GPUクラウドの最有力プロバイダーとして位置付ける一方、Trainiumなど独自コンピュートの選択肢も維持することで顧客の柔軟性を確保する狙いがある。対象領域はエージェント型AIや科学的発見、企業の業務自動化に加え、Amazon Roboticsとの連携による倉庫自動化、さらに連邦政府向けAI・国家安全保障インフラにまで及んでおり、ハイパースケーラー各社によるAI基盤投資競争が一段と激化していることを示している。
