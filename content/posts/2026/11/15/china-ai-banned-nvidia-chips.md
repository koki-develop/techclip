---
date: "2026-11-15T08:06:47+09:00"
title: "モデル重みの「指紋」でBlackwell使用が発覚、中国AI大手4社が輸出規制違反の疑い"
description: "元OpenAIエンジニアによるフォレンジック分析で、DeepSeekなど中国AI大手の最新モデルが輸出禁止のNvidia Blackwell GPUで訓練された痕跡が見つかり、米国の対中輸出規制の実効性に疑問が投げかけられている。"
tags:
  - AI
  - Other
references:
  - "https://techcrunch.com/2026/11/13/export-banned-nvidia-chips-are-behind-chinas-most-powerful-ai-models-uh-oh-jensen/"
  - "https://www.theregister.com/ai-and-ml/2026/11/13/chinese-ai-labs-are-training-models-on-nvidias-blackwell-despite-export-controls-says-ex-openai-engineer/5309891"
---

## 概要

元OpenAIエンジニアでAI研究団体Unemployment Labsを主宰するWill DePue氏が、DeepSeek、Moonshot AI、MiniMax、Ant Groupといった中国の主要AIラボが公開した最新モデルの重みに、米国の輸出規制対象であるNvidia製Blackwell GPUの「指紋」が残っていることをフォレンジック分析で明らかにした。密輸の実行経路を直接証明するものではないとの留保はあるものの、対中輸出規制が実質的に機能していない可能性を示す有力な状況証拠として注目されている。

## どうやって突き止めたのか

DePue氏の手法は、PyTorchがモデルの重みを初期化する際に用いる擬似乱数生成アルゴリズム「Philox」の決定性に着目したものだ。GPUのアーキテクチャと乱数シードの組み合わせごとに一意の初期重みパターンが生成され、そのパターンは学習後に公開されたモデルにも痕跡として残る。同氏は「6兆通り以上のチップ構成とシード番号の組み合わせを探索し、公開されている重みモデルと照合した」と説明している。この分析により、DeepSeek-V4-Pro、Kimi K3、MiniMax-M3を含む6つの中国モデルがBlackwell系システムで訓練された痕跡を持ち、うち4つはNvidiaの液冷ラックシステムであるGrace Blackwell(GB200/GB300)に特有の構成と一致したという。

## 輸出規制の実効性への疑問

この発見は、米国の対中輸出規制に大きな抜け穴があることを浮き立たせている。報道によれば、2024年から2025年にかけて約27万5000台のNvidia製アクセラレータがマレーシア経由で流入し、中国企業がオフショアのデータセンターを利用して規制を回避しているとみられる。ある専門家は「マレーシアに行きさえすれば何でもできる」と規制の緩さを指摘した。密輸を通じて中国に流入した先進チップは累計で約200万個規模との推計もあり、香港では約60万個のH200チップが輸入承認を待って保管されているとも報じられている。チップ流通を担うシンガポール拠点のMegaspeed社が密輸疑惑で米国とシンガポール両政府の捜査対象となっているなど、供給網の管理体制そのものにも疑念が持たれている。

## 今後の展望

この一連の報道を受け、米議会ではAI Overwatch Act、Chip Security Act、Match Act、Cloud Security Actなど、輸出規制を強化する複数の法案が勢いを増している。一方で、米国内のクラウド事業者経由で規制対象チップの性能を利用する手法は明確に禁止されていないなど、抜け穴は残る。中国側は今回の一件を機に、Nvidiaチップの輸入解禁を求めるよりも自国製半導体の開発を加速させる可能性もあり、そうなればNvidiaが見込んでいた中国市場からの将来的な収益が失われることになる。
