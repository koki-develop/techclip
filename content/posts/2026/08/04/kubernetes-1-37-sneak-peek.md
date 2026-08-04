---
date: "2026-08-04T14:56:13+09:00"
title: "Kubernetes v1.37の変更点先行公開、kubectl runの一部フラグ非推奨化やipvsモード段階的廃止へ"
description: "Kubernetesプロジェクトが次期v1.37の主な変更点を予告し、kubectl runのfilenameフラグ非推奨化、Static PodのAPIリソース直接参照禁止、kube-proxyのipvsモード段階的廃止などが明らかになった。"
tags:
  - Cloud
references:
  - "https://kubernetes.io/blog/2026/07/31/kubernetes-v1-37-sneak-peek/"
---

## 概要

Kubernetesプロジェクトは7月31日、次期バージョンv1.37で予定されている主な変更点を公式ブログで先行公開した。今回のリリースでは大型の新機能追加よりも、既存機能の非推奨化や整理が中心となっており、`kubectl run`コマンドの`--filename`（`-f`）フラグの非推奨化、Static PodからのSecret/ConfigMapへのAPIリソース直接参照の禁止、そしてkube-proxyのipvsモードの段階的廃止という3つの変更が柱となっている。いずれもすぐに動作が壊れるものではないが、クラスター管理者やスクリプトの保守者は早めに対応を計画しておく必要がある。

## kubectlとStatic Podの変更

`kubectl run`の`--filename`フラグは、生成されるPodが常にコマンドライン引数（Pod名や`--image`など）から構築される仕様上、ファイル指定自体に意味がないという理由から非推奨化される。代替コマンドの使用が想定されるが、公式ブログでは具体的な置き換え先は明示されていない。

またkubeletでは、APIサーバーを経由せずノード上の設定ファイルから直接生成されるStatic Podについて、`configMapRef`や`secretRef`などのフィールドを用いたAPIリソースへの参照が厳密に禁止される。Static PodはAPIリソースへのアクセスを前提とした設計になっておらず、これまでバグによりconfigMapRef/secretRefでの参照が実際には機能せず黙って無視される状態だったものを是正する措置で、これに伴い暫定的な回避手段だった`PreventStaticPodAPIReferences`フィーチャーゲートも削除される。該当する設定を使っている場合は、Static Podでの直接参照ができなくなるため、他の方法での対応を検討する必要がある。

## kube-proxy ipvsモードの段階的廃止

もう一つの大きな変更が、kube-proxyのipvsモードの非推奨化だ。ipvsモードはv1.8で、iptablesモードのパフォーマンス課題を解決する目的で導入された経緯があるが、カーネルのIPVS APIだけではKubernetes Servicesの仕様を完全に実装できず、内部的にはiptablesにも依存し続けているという構造的な問題を抱えていた。この点は「KEP-3866」でも指摘されており、iptables・ipvs双方の課題を解決する後継としてnftablesベースのプロキシ実装が進められている。

廃止はv1.37から段階的に進む。v1.37ではログに非推奨警告が出力されるのみでデフォルトの動作は変わらないが、v1.40でipvsモードがデフォルト無効化（フィーチャーゲート経由での有効化は可能）され、v1.43でサポートが完全に削除される予定だ。現在ipvsモードを利用しているクラスターの管理者は、`kubectl -n kube-system get configmap kube-proxy -o jsonpath='{.data.config\.conf}'`などでモード設定を確認し、iptablesモードやnftablesモードへの移行計画を早めに立てておくことが望ましい。

## 今後の展望

今回予告された変更はいずれも即座に破壊的な影響を及ぼすものではないが、v1.37はこれらの非推奨化サイクルの起点となる。特にipvsモードの廃止は複数バージョンにまたがる長期計画であり、大規模クラスターほど移行に時間を要する可能性がある。あわせて、cgroup v1のサポート廃止も継続中の課題として挙げられており、モダンなLinuxディストリビューションとcontainer runtimeへの更新が引き続き推奨されている。正式なv1.37のリリースノートは今後公開される予定で、詳細な移行ガイドの追跡が求められる。
