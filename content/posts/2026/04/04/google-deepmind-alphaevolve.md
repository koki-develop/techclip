---
date: "2026-04-04T10:37:37+09:00"
title: "Google DeepMindのAlphaEvolve、LLMでゲーム理論アルゴリズムを自律進化させ専門家設計を超える"
description: "Google DeepMindがAlphaEvolveをゲーム理論に応用し、Gemini 2.5 Proが自律的に設計したVAD-CFR変種が11ゲーム環境のうち10で人間専門家のアルゴリズムを上回ることを実証した。"
tags:
  - AI
references:
  - "https://www.marktechpost.com/2026/04/03/google-deepminds-research-lets-an-llm-rewrite-its-own-game-theory-algorithms-and-it-outperformed-the-experts/"
  - "https://deepmind.google/blog/alphaevolve-a-gemini-powered-coding-agent-for-designing-advanced-algorithms/"
---

## 概要

Google DeepMindは、2025年5月に発表したLLM駆動型のアルゴリズム自律設計エージェント「AlphaEvolve」を多人数強化学習（MARL）のゲーム理論アルゴリズムに応用した研究成果を公開した。Gemini 2.5 Proを活用して生成されたアルゴリズム変種「VAD-CFR」は、ポーカーのような不完全情報ゲームを含む11のゲーム環境のうち10において、人間の専門家が手動で設計した最先端アルゴリズムを上回る性能を示した。LLMが単なるコード生成にとどまらず、アルゴリズムの本質的な改善を自律的に行えることを示した点で業界の注目を集めている。

## AlphaEvolveの仕組みとゲーム理論への応用

AlphaEvolveは「LLMの創造的な問題解決能力」と「自動検証システム」を組み合わせた進化的フレームワークだ。数値パラメータではなくソースコード自体を変異・進化させる点が特徴で、Gemini Flashが多様なアイデアを高速に探索し、Gemini Proがより深い洞察を提供する役割を担う。

今回の研究では、ゲーム理論の2大アルゴリズムパラダイムに適用された。まず**CFR（Counterfactual Regret Minimization）**への応用として、AlphaEvolveが発見した「VAD-CFR」は、従来の静的な割引係数に代わりEWMA（指数加重移動平均）で瞬間的な後悔の大きさを追跡し、割引係数を動的に調整する「ボラティリティ認識型割引」を採用する。さらにポリシー平均化を500イテレーションまで遅延させるという人間には直感的でない設計も自律的に導き出した。次に**PSRO（Policy Space Response Oracles）**への応用では、AlphaEvolveが「SHOR-PSRO」を発見した。これはOptimistic Regret MatchingとSoftmax純粋最良戦略コンポーネントの間でブレンド係数をアニーリングし、貪欲な活用からロバストな均衡探索への移行を自動化する手法で、従来は専門家が手動でチューニングする必要があった部分を排除した。

## AlphaEvolveの既存の実績と応用の広がり

AlphaEvolveはゲーム理論以前にも、数学とコンピューティングの分野で顕著な成果を上げている。Googleのデータセンタースケジューリングの最適化でコンピュートリソースの0.7%を回復し、Geminiのトレーニング時間を1%短縮、FlashAttentionの実装では最大32.5%の高速化を達成した。数学的成果としては、Strassen法（1969年）以来未改善だった4×4複素行列乗算を48スカラー乗算で実現し、11次元のキッシング数問題で新たな下限を確立するなど、約50の未解決問題の20%で既知の最良解を更新した。

今回のゲーム理論への応用は、AlphaEvolveが特定分野に特化せず「汎用的なアルゴリズム設計システム」として機能することを改めて実証したものだ。DeepMindは今後、材料科学、創薬、サステナビリティなどの分野への展開も見据えており、LLMによる自律的なアルゴリズム設計が科学研究の加速に貢献する可能性を示している。
