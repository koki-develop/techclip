---
date: "2026-04-15T18:29:59+09:00"
title: "NVIDIA、ヒューマノイドロボット向けオープンVLAモデル「GR00T N1.6」と推論モデル「Cosmos Reason 2」を発表"
description: "NVIDIAがロボット向けオープンモデル「Isaac GR00T N1.6」と「Cosmos Reason 2」を発表し、Hugging Faceで公開。32層の拡散トランスフォーマーによる全身制御と256Kトークンの長文脈推論でヒューマノイドロボットの実用化を加速する。"
tags:
  - AI
references:
  - "https://investor.nvidia.com/news/press-release-details/2026/NVIDIA-Releases-New-Physical-AI-Models-as-Global-Partners-Unveil-Next-Generation-Robots/default.aspx"
  - "https://www.therobotreport.com/nvidia-releases-new-physical-ai-models-plus-autonomous-vehicle-tools/"
  - "https://aibusiness.com/robotics/nvidia-launches-physical-ai-models"
---

## 概要

NVIDIAは2026年1月5日（CES 2026）、ロボット向け新オープンAIモデルとして「Isaac GR00T N1.6」および「Cosmos Reason 2」を発表した。Isaac GR00T N1.6はヒューマノイドロボット向けに設計されたビジョン・言語・アクション（VLA）モデルであり、自然言語指示と視覚情報を統合してロボットの全身制御を実現する。両モデルはHugging Faceでオープンモデルとして公開されており、研究者や開発者が自由に利用・ファインチューニングできる。この発表はBoston Dynamics、LG Electronics、NEURA Roboticsなど世界の主要ロボットメーカーが次世代ロボットを披露するタイミングに合わせて行われた。

## Isaac GR00T N1.6の技術的詳細

Isaac GR00T N1.6は、前世代モデルの2倍となる32層の拡散トランスフォーマーを搭載し、よりスムーズで安定したロボット動作を生成する。エゴセントリックカメラからの視覚ストリーム、ロボットの状態情報、自然言語指示を統合し、統一されたポリシー表現として処理することで、ヒューマノイドの歩行と物体操作を同時にこなす「全身制御（whole-body control）」が可能になった。

モデルはヒューマノイド、モバイルマニピュレーター、バイマニュアルアームを含む複数のロボットプラットフォームから収集した1万時間以上のロボット操作データで事前学習されており、異なるロボット機体への転用（クロス・エンボディメント）にも対応している。シミュレーション環境「Isaac Lab」での強化学習により生成された動作プリミティブと、Cosmos Reason 2Bによる視覚・言語理解を組み合わせることで、シミュレーションから実環境へのゼロショット転用も実証されている。Hugging Faceでは「nvidia/GR00T-N1.6-3B」として公開されており、Hugging FaceのLeRobotライブラリとも統合されている。

## Cosmos Reason 2の機能と仕様

Cosmos Reason 2は物理AI向けの推論特化型ビジョン言語モデル（VLM）であり、2Bと8Bの2種類のパラメータサイズで提供される。最大入力トークン数は前世代の16Kから大幅に拡張され256Kとなり、長い動画やシーケンスの文脈理解が可能になった。空間認識能力も強化されており、2D・3Dの点ローカライゼーション、バウンディングボックス座標の抽出、軌跡データの解析、OCRによるテキスト認識に対応している。

Isaac GR00T N1.6において、Cosmos Reason 2B変種が「脳」として機能し、高レベルの指示をシーン理解に基づいた具体的な行動ステップに分解する役割を担う。また単独のモデルとしても幅広い用途に活用されており、Salesforceの職場安全分析ロボット、Uberの自動運転車訓練データのビデオキャプション（BLEUスコアを10.6%改善）、Hitachiの交通・安全監視システムなどへの採用事例が発表されている。

## パートナーシップとエコシステムの拡大

今回の発表に合わせて、NVIDIAはロボティクス向けのハードウェアとツール群も拡充した。新型モジュール「Jetson T4000」は前世代比4倍の性能となる1,200 FP4 TFLOPSと64GBメモリを70ワットの消費電力で実現し、1,000ユニット規模の量産価格は1,999ドルに設定されている。加えて、ロボット評価向けオープンソースベンチマークフレームワーク「Isaac Lab-Arena」、開発ワークフロー向けクラウドオーケストレーション「OSMO」、世界モデル群「Cosmos Transfer 2.5 / Predict 2.5」も同時に発表された。

Hugging Faceのオープンソースヒューマノイドロボット「Reachy 2」はNVIDIA Jetson Thorロボティクスコンピュータと完全に相互運用可能となり、GR00T N1.6を含む任意のVLAモデルを実行できるようになる。NVIDIAはこの一連の動きを「ロボティクスのAndroid」を目指す戦略の一環と位置付けており、オープンなエコシステムの構築によって自律ロボットの産業利用を加速させる方針を示している。
