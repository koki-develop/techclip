---
date: "2026-09-23T18:14:31+09:00"
title: "Next.jsのImageResponseに緊急パッチ、CVSS9.5のリモートコード実行脆弱性CVE-2026-94545を修正"
description: "Next.jsのImageResponse機能(next/og)に細工されたSVG入力でリモートコード実行が可能な重大脆弱性CVE-2026-94545が見つかり、v16.3.6とv15.5.26が緊急リリースされた。"
tags:
  - Programming Languages
  - Security
references:
  - "https://nextjs.org/blog/nextjs-security-update-september-22-2026"
  - "https://thehackernews.com/2026/09/critical-nextjs-imageresponse-flaw-can.html"
  - "https://www.netlify.com/changelog/2026-09-22-nextjs-imageresponse-vulnerability/"
---

## 概要

Vercelが開発するReactフレームワークNext.jsに、深刻度が最高クラスの脆弱性が見つかった。動的にOGP画像などを生成する`ImageResponse`機能(`next/og`)において、細工されたSVG入力を与えることでNode.jsランタイム上でリモートコード実行(RCE)が可能になるというもので、CVE-2026-94545として登録され、CVSSスコアは9.5(重大)と評価されている。Vercelは9月22日、この問題に対処する緊急のアウトオブバンド・セキュリティアップデートとしてv16.3.6(Active LTS)およびv15.5.26(Maintenance LTS)をリリースし、ユーザーに即時アップデートを呼びかけた。

## 技術的な詳細と影響範囲

脆弱性の根本原因は、`ImageResponse`がレイアウトをSVGに変換する際に利用しているライブラリSatoriにある。URLパラメータなど攻撃者が制御可能な値がSVGのコンテンツ・属性・スタイルとして渡される際、出力段階で適切にエスケープされずにSVGコード自体として解釈されてしまうケースがあり、これが上流の別の依存関係の脆弱性と組み合わさることでコード実行に至る。Vercel自身の公式アドバイザリ(GHSA-vcvr-r3jv-pc5j)およびSatori側のアドバイザリ(GHSA-wx4j-mvgx-mqwp)によれば、影響を受けるのはNext.js 16.2.0以上16.3.6未満でNode.jsランタイム上の`ImageResponse`を利用している場合に限られる。Edgeランタイム版の`ImageResponse`は影響を受けず、また15系はRCEの対象外だが、15.5.26には念のための追加のセキュリティ強化が施されている。

## 対応状況と推奨アクション

修正はシンプルで、16.3系ユーザーは`npm install next@16.3.6`、15.5系ユーザーは`npm install next@15.5.26`でアップグレードし再デプロイすればよい。即座のアップデートが難しい場合の暫定策として、攻撃者が制御できる値をNode.jsの`ImageResponse`が生成するSVGコンテンツから排除するか、XMLとして適切にエスケープすることが推奨されている。ホスティング事業者のNetlifyも同日中に注意喚起を発表し、自社インフラ上では影響が関数呼び出しのクラッシュにとどまり、コード実行までは至らないと説明しつつも、`ImageResponse`を使い信頼できない入力(テキストやリクエスト経由で読み込む画像など)を画像生成に利用しているユーザーに対し、直ちにアップグレードして再デプロイするか、脆弱なデプロイプレビューを手動で削除するよう促している。

## 今後の展望

The Hacker Newsの報道によれば、2026年9月23日時点で公開されているエクスプロイトコードや実際の悪用事例は確認されていない。ただし、CVSS9.5という評価の高さと、`ImageResponse`がOGP画像生成などで広く使われる機能であることを踏まえると、パッチ未適用の環境は早期に攻撃対象となるリスクがある。今回の一件は、フレームワークが内部で利用するSVGレンダリングライブラリなど、間接的な依存関係の脆弱性がアプリケーション全体の安全性に直結し得ることを改めて示した事例といえる。
