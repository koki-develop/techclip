---
date: "2026-10-06T18:15:12+09:00"
title: "TC39東京会合、イテレータ操作を強化する3提案がStage4到達、evalのセキュリティ強化提案はStage4入りを提案"
description: "TC39第116回会合(東京)で「Iterator Join」「Iterator Includes」「Iterator Chunking」の3提案がStage4(仕様確定)に到達した。「Dynamic Code Brand Checks」もStage4入りを目指して提案されたが、現時点ではStage3のままである。"
tags:
  - Programming Languages
references:
  - "https://github.com/tc39/agendas/blob/main/2026/09.md"
  - "https://github.com/tc39/proposal-iterator-join"
  - "https://github.com/tc39/proposal-iterator-includes"
  - "https://github.com/tc39/proposal-iterator-chunking"
  - "https://github.com/tc39/proposal-dynamic-code-brand-checks"
---

## 概要

ソニー主催で9月29日から10月1日にかけて東京で開催されたTC39(ECMAScript標準化委員会)の第116回会合で、「Iterator Join」「Iterator Includes」「Iterator Chunking」の3提案がStage3からStage4(仕様確定)へ進んだ。Stage4はTC39のプロセスにおける最終段階であり、ECMA262仕様書へのプルリクエストがマージされることで、次期ECMAScript仕様への正式な組み込みが確定する。これら3つはいずれもイテレータ操作を拡充するものだ。evalや`Function`コンストラクタを使った動的コード実行のセキュリティ制御を強化する「Dynamic Code Brand Checks」もStage4入りを目指して提案されたが、現時点ではStage3のまま残っている。

## イテレータ操作を拡充する3提案

`Iterator.prototype.join()`を追加する「Iterator Join」(チャンピオン: Kevin Gibbons)は、`Array.prototype.join()`と同様の挙動をイテレータに対して提供する。従来、配列以外のイテラブルの要素を文字列として連結するには、`Iterator.from(it).reduce()`で中間文字列を都度生成するか、`Array.from(it).join()`で配列に変換してから結合する必要があり、いずれも余分なコストが発生していた。`join()`をイテレータプロトタイプに直接実装することで、この非効率を解消する。

「Iterator Includes」(チャンピオン: Michael Ficarra)は、`Array.prototype.includes()`に相当する`includes()`をイテレータに追加する。比較には`Array.prototype.includes`と同じSameValueZeroアルゴリズムを採用し、検索開始位置を指定する`fromIndex`引数もサポートする(負の値には未対応)。これまで同等の処理は`some()`で代替する必要があったが、`includes()`により意図がより直接的に表現できるようになる。

「Iterator Chunking」(チャンピオン: Michael Ficarra)は、イテレータの要素を部分列として扱う`chunks()`と`windows()`を追加する。`chunks()`は要素を重複なく指定サイズごとにグループ化するもので、ページネーションやカレンダーのような格子レイアウト、バッチ処理への応用が想定されている。一方`windows()`は指定サイズのスライディングウィンドウを生成し、移動平均の計算やペアワイズ比較といった、連続する要素間の関係を扱うアルゴリズムに向く。いずれもRust・Python・Haskellなど他言語や既存のJavaScriptライブラリで広く使われてきた機能で、その実績を踏まえて仕様が設計された。

## 動的コード実行のセキュリティを強化する提案

「Dynamic Code Brand Checks」(チャンピオン: Nicolò Ribaudo)は、`eval()`や`new Function()`による動的コード評価を、ホスト環境がより細かく制御できるようにする提案だ。現状のJavaScriptには3つの制約がある。まず`eval()`は文字列以外の引数を受け付けないため、事前に検証済みのオブジェクトとしてコードを渡す仕組みがない。また、ホスト側の検証フック`HostEnsureCanCompileStrings`に渡される情報が限定的で、文脈に応じた細かい信頼判定ができない。さらに、`Function`コンストラクタではパラメータと本体が分離された状態で検証が行われるため、完全なコード文字列を検証できないという問題もあった。

この提案では`HostGetCodeForEval()`という新たなホスト用フックを導入し、コードを表すオブジェクトから文字列を取り出せるようにするとともに、`HostEnsureCanCompileStrings`に渡す文脈情報を拡張する。これにより、ブラウザなどのホスト環境は、Content Security Policy(CSP)の`unsafe-eval`のようにevalを一律禁止するのではなく、W3CのTrusted Types仕様と連携しながら、事前に検証済みのコードオブジェクトに限って動的評価を許可するといった、段階的なセキュリティ制御を実装できるようになる。`({}[x][x](y)())`のようにコードレビューで見逃されやすい迂回パターンへの対策としても意義がある。既存プログラムの挙動は変えない後方互換の設計だ。

## 今後の見通し

Stage4への到達はECMAScript仕様そのものへの採用を意味するが、実際にJavaScriptエンジンで利用できるようになるまでには、各ブラウザ・ランタイムでの実装とテストが別途必要になる。イテレータ関連の3提案は配列の既存メソッドとの一貫性を重視した設計になっており、学習コストを抑えつつ実務での利用が広がることが見込まれる。Dynamic Code Brand Checksは、CSPやTrusted Typesとともに運用することで、動的コード実行を伴うアプリケーションのセキュリティ水準を高める基盤となりそうだ。
