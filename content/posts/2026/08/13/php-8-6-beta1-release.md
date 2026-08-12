---
date: "2026-08-13T08:12:37+09:00"
title: "PHP 8.6.0 Beta 1が公開、部分関数適用とネイティブポーリングAPIで「厳格化路線」を鮮明に"
description: "PHP 8.6.0のBeta 1が公開され、部分関数適用やIo\\Pollネイティブポーリング、Time\\Durationクラスの追加とともに、標準ライブラリ全体でエラー処理が厳格化された。"
tags:
  - Programming Languages
references:
  - "https://www.linuxcompatible.org/story/php-860-beta-1-partial-function-application-native-polling-and-stricter-error-handling"
---

## 概要

PHP開発チームは8月11日、次期メジャーバージョンとなるPHP 8.6.0のBeta 1をJoe Ferguson氏名義でタグ付け・公開した。PHP 8.5.0のリリースからおよそ9カ月というこれまで通りのリリースサイクルに沿ったもので、目玉となるのは部分関数適用(Partial Function Application)、ストリーム多重化を刷新するネイティブポーリングAPI「Io\\Poll」、そしてナノ秒精度の時間間隔を扱う`Time\\Duration`クラスの3つの新機能だ。これに加えて、標準ライブラリ全体でエラー処理を厳格化する変更が数多く盛り込まれており、記事は今回のリリースを「PHPの厳格化時代の到来」と表現している。

## 主な新機能

部分関数適用は、引数の一部を`?`というプレースホルダーで残し、`...`で残余引数をまとめて受け取れるようにする機能で、部分的に適用した関数オブジェクトを生成できる。型ヒントや戻り値の型はリフレクションを通じて保持される仕組みで、対応するRFCは33対0という圧倒的多数で可決された。

`Io\\Poll`は、長らく使われてきた`stream_select()`を置き換えるネイティブI/O APIで、LinuxのepollやmacOS/BSDのkqueue、Solarisのevent ports、WindowsのWSAPollといった各プラットフォーム固有の仕組みを内部で使い分けて最適化を図る。あくまで「ポーリング機構であり、完全なイベントループではない」点が特徴だが、ReactPHPやAmpHP、Revoltといった非同期処理ライブラリがバックエンドとして採用していくとみられている。

もう一つの目玉である`Time\\Duration`は、finalかつreadonlyなクラスとしてナノ秒精度の時間間隔を扱えるようにするもので、ISO 8601形式のパースに対応し、`sleep()`とも直接連携できる。

## エラー処理の厳格化と非推奨機能

PHP 8.6では、これまで黙って処理を続けてきた挙動の多くが例外を投げるように変更される。たとえば文字列引数中のNULバイトはこれまで暗黙に切り詰められていたが、今後は`ValueError`が送出される。`array_filter()`は不正なモード指定を拒否するようになり、`pathinfo()`や`scandir()`も失敗時に静かに処理を続けず明示的にエラーを出すようになった。`sleep()`や`usleep()`もプラットフォームの上限値でクランプされる。

セキュリティ関連のデフォルト設定も変更され、`session.use_strict_mode`、`session.cookie_httponly`はいずれもデフォルトで1に、`session.cookie_samesite`はデフォルトで`Lax`になる。このほか、戻り値を無視すると問題が起きうる関数に付与する`#[\\NoDiscard]`属性、スタンドアロン関数としての`clone()`、クラス定数やenumケースにも対応した`#[\\Override]`属性の拡張、コンストラクタプロモートプロパティへの`final`修飾子の適用、参照返しに対応したパイプ演算子の強化なども追加される。

非推奨化の対象としては、MbregexおよびOnigurumaバックエンド、`metaphone()`、`is_double()`、`doubleval()`、`spl_classes()`や`spl_object_hash()`などのSPL関数が挙げられているほか、GMP演算子は暗黙の切り捨て挙動を失う。今回のBeta 1でAPIや挙動の変更点は概ね出そろった形であり、今後のリリース候補(RC)を経て正式版のリリースに向けて安定化が進む見通しだ。
