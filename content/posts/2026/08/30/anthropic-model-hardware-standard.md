---
date: "2026-08-30T18:12:02+09:00"
title: "Anthropic、AIエージェントが実験機器を操作する新標準「Model Hardware Standard」発表 レーザー安定化は25倍高速化"
description: "AnthropicがAIエージェントによる物理機器の安全な操作・連携を可能にする新標準「Model Hardware Standard」のリサーチプレビューを発表し、Genentechやカーネギーメロン大学などでの検証成果を公開した。"
tags:
  - AI
references:
  - "https://www.anthropic.com/news/model-hardware-standard-research-preview"
  - "https://www.cnbc.com/2026/08/27/anthropic-pushes-into-physical-world-with-new-standard-to-help-ai-agents-operate-machines.html"
  - "https://fortune.com/2026/08/27/anthropic-makes-first-move-into-physical-ai-with-universal-standard-for-scientists-manufacturing/"
---

## 概要

Anthropicは8月27日、AIエージェントがロボットアーム、顕微鏡、液体分注装置といった物理機器を安全に操作・連携できるようにする新標準「Model Hardware Standard(MHS)」のリサーチプレビューを発表した。HHMI Janelia Research Campusと共同開発したもので、異なるベンダーの機器を統合する作業が従来は数週間から数ヶ月かかっていたのに対し、MHSを使えば数時間から数分に短縮できるという。Claudeに限らずOpenAIのモデルやオープンソースモデルなど、あらゆるLLMに対応するモデル非依存の設計である点も特徴だ。Nvidia CEOのJensen Huangが「将来はすべての産業企業がロボティクス企業になる」と予測してきたように、AIとロボティクス・物理機器の融合が業界全体で加速する中、Anthropicにとって物理AI分野への初の本格参入となる。

## 技術的な仕組み

MHSは、2024年発表のオープン標準Model Context Protocol(MCP)をベースにしており、Anthropicの技術者は「AIとソフトウェアをつなぐUSBのような存在」と表現している。標準化されたドライバーを軸に、機器の値を取得する「読み取り」や値を設定する「書き込み」といったプリミティブなコマンド、標準フォーマットによるデバイス発見、さらに機器の重量や耐荷重といった物理特性を自然言語タグとして記述しエージェントに安全な操作方法を理解させる仕組みなどで構成される。制御方式はMCP、コマンドラインインターフェース、コードファイル(API)の3通りから選べる。これによりエージェントは実験手順を実行しながら複数デバイスから運用データを受信し、結果を監視してパラメータをリアルタイムに調整できるようになる。

## 検証パートナーの成果

創薬企業Genentechでは、液体ハンドラー、ロボットアーム、プレートリーダーを連携させたタンパク質定量測定において、Claudeは当初、気泡による誤差の原因を自ら理解できず、研究者から気泡発生を教えられた後、流速を最適化した(水は毎秒140マイクロリットル、粘性の高いタンパク質は毎秒10マイクロリットルなど)。カーネギーメロン大学では通常数週間かかる自動化セットアップをわずか8時間で構築し、意図的に発生させたプレート欠損やカメラ切断など6種の障害をすべて安全に検知・停止させた。量子コンピューティング企業QuEra Computingでは、チタンサファイアレーザーの周波数ロック回復について、従来手法の150秒・成功率58%に対し、MHS導入後は6秒・成功率99.3%(700回中695回成功)という大幅な改善を報告している。ワシントン大学の研究室ではqPCRの増幅曲線をリアルタイム分析して最適な停止タイミングを判断させ、6台の機器を1週間以内に接続した(従来は数ヶ月を要した)。

## 今後の展開と課題

Amazon Web Servicesはロボット向けライブラリ「Strands Robots」を通じてMHSに対応するほか、Automata、Danaher、Doosan Robotics、Tecan、Universal Robots、QIAGENといった装置・ロボティクス各社が対応を進めている。一方でAnthropicは、Claudeが気泡形成などの物理現象を直感的に理解する能力にはまだ限界があることや、対応インターフェースを持たない従来型機器への未対応、長時間のエージェント稼働に伴う計算コストといった課題も認めている。現時点では研究プレビュー段階であり、Anthropicは今後、安全な展開に向けたガイダンスを公開し、物理安全のロードマップを策定した上でオープンソース化する計画だ。参加を希望する企業や研究機関は専用サイトでウェイトリスト登録を受け付けている。
