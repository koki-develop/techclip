# GPU上で高速動作しAIによる誤った変更を「形式的証明」で防ぐ新言語「Bend」
Tags: Programming Languages, AI

- Bend is a high-speed programming language that runs on GPUs and prevents AI errors through 'proofs' (2026-09-30)
  https://gigazine.net/gsc_news/en/20260930-bend-lang/

HigherOrderCoが開発する新言語「Bend」(Bend 2)が注目を集めている。GPU上でC言語並みの実行速度を実現しつつ、「LAWS.bend」というファイルにLeanベースの形式的証明ルールを記述することで、AIコーディングエージェントによるコード変更が既存の不変条件を破らないことを型検査器が保証する仕組みを備える。AIエージェントによる自動コード変更が広がる中、安全性を担保する新たなアプローチとして紹介されている。
