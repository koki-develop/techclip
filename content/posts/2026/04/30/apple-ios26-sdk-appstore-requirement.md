---
date: "2026-04-30T02:37:03+09:00"
title: "Apple、App StoreへのiOS 26 SDK提出を義務化——Liquid Glassデザインが既存アプリに自動適用"
description: "Appleは2026年4月28日より、App Store ConnectへのすべてのアプリをiOS 26 SDK以降でビルドすることを必須とした。"
tags:
  - Other
references:
  - "https://developer.apple.com/news/?id=ueeok6yw"
---

## 概要

Appleは2026年4月28日より、App Store Connectへの新規アプリおよびアップデートに対し、最新のSDKでのビルドを義務付けた。具体的には、iOS・iPadOSアプリはiOS 26 SDK（またはiPadOS 26 SDK）以降、tvOSアプリはtvOS 26 SDK以降、visionOSアプリはvisionOS 26 SDK以降、watchOSアプリはwatchOS 26 SDK以降でのビルドが必要となる。開発にはXcode 26が必要であり、開発者はツールチェーンのアップデートも求められる。この要件は2026年2月3日に事前告知されており、開発者には約3か月の準備期間が設けられていた。

## Liquid Glassデザインの自動適用と開発者への影響

iOS 26 SDKでビルドを行うと、Appleが新たに導入した「Liquid Glass」デザイン言語が既存のUIコンポーネントに自動的に適用される。Liquid Glassはガラス素材のような透過・反射効果を活かした視覚スタイルで、ナビゲーションバー・タブバー・モーダルなどの標準UIパーツの外観を刷新するものだ。既存アプリがこのSDKでリビルドされると、意図せずUIの見た目が変わる可能性があり、開発者コミュニティではレイアウト崩れや独自デザインへの影響を懸念する声が上がっている。特に、独自のビジュアルスタイルを持つアプリや、細かなUIチューニングを施したアプリほど、新デザインシステムとの整合性確認に工数がかかるとみられる。

## 開発者が取るべき対応

Appleのガイドラインに準拠するためには、Xcode 26へのアップデートと各プラットフォームSDKへの対応が必須となる。具体的な対応手順としては、まずXcode 26でビルドターゲットをiOS 26 SDK以降に更新し、実機・シミュレータ上でLiquid Glassが適用された状態のUIを十分にテストすることが推奨される。TestFlightを活用したベータテストを経てから本番提出することで、デザイン崩れを事前に検知しやすくなる。Appleのガイドに従いつつ、Human Interface Guidelinesを参照して新デザイン言語に適応したUI調整を行うことが、スムーズな移行への近道となる。
