---
date: "2026-11-19T18:09:43+09:00"
title: "PHP 8.6が正式リリース、部分適用やDuration・Polling APIで「高速・安全・高機能」を標榜"
description: "PHP公式チームがPHP 8.6を正式リリースし、部分適用やナノ秒精度のDurationクラス、新しいPolling APIなどを追加した。"
tags:
  - Programming Languages
references:
  - "https://www.php.net/releases/8.6/en.php"
  - "https://developer.wordpress.org/news/2026/11/whats-new-in-php-8-6-and-what-that-means-for-wordpress/"
---

## 概要

PHP公式チームは11月19日、PHP 8.6を正式リリースした。「Faster, Safer, More Powerful」を掲げる今回のリリースでは、関数の一部引数を固定して新しい関数（Closure）を作る「部分適用(Partial Function Application)」、ナノ秒精度で時間を扱う`\Time\Duration`クラス、epoll/kqueue/event ports/WSAPollなど各OSのネイティブ機構を使う新しい`Io\Poll`、値を指定範囲に収める`clamp()`関数などが新たに追加された。WordPress開発者向けメディアの記事によれば、新機能として1つのINIディレクティブ、15のenum、17の関数、24のクラス、47の定数、1つのインターフェースが追加され、27の関数に改善が加えられている。

## 主な新機能

部分適用は`?`や`...`といったプレースホルダーを使い、関数の一部引数だけを先に渡してClosureを返す機能で、`array_filter`などへのコールバック指定を簡潔に書けるようにする。`\Time\Duration`はタイムゾーンに依存せずナノ秒精度で経過時間を表現でき、250年以上の期間も表現可能で、タイムアウトやベンチマーク計測に向く。`Io\Poll`は`stream_select()`の制限を受けずに複数のストリームを効率的に監視できるAPIで、ReactPHPやAmPHPのようなイベントループ実装を見据えた設計になっている。また`clamp()`は数値だけでなく`Time\Duration`のようなオブジェクトにも適用でき、`SortDirection`enumの追加でソート順を型安全に表現できるようになった。readonlyプロパティへのデフォルト値指定や、関数パラメータ単位のDocComment、`ReflectionProperty`の`isReadable()`/`isWritable()`メソッドなど、開発体験に関わる改善も多く含まれる。パフォーマンス面では、`array_map()`とfirst-classコールバブル／部分適用の組み合わせがループへコンパイルされるようになるほか、`printf()`の高速化、ステートレスClosureのキャッシュ、JSONエンコードの高速化が挙げられている。

セキュリティ関連では、Sodium拡張にポスト量子暗号（X-Wing、ML-KEM-768）やIP暗号化、SHAKE/TurboSHAKEが追加され、TLSのセッション再開や外部PSK、TLS 1.3の0-RTTサポートも加わった。一方で、`return`を`finally`ブロック内で使う記法や`__construct()`/`__destruct()`からの戻り値、`mb_ereg()`や`mb_split()`などのOniguruma系mbstring正規表現関数、`is_double()`系の別名関数、`spl_object_hash()`などが非推奨となった。`trim()`系関数がフォームフィード(`\f`)を除去するようになる変更や、`fclose()`・`file_put_contents()`・`copy()`がフラッシュ・クローズ失敗時に`false`を返すようになる変更、多くの関数が範囲外の値に対して`ValueError`を投げるようになる変更など、破壊的変更も少なくない。セッションもデフォルトでより安全になり、`session.use_strict_mode`や`session.cookie_httponly`が有効化され、`session.cookie_samesite`は`Lax`に設定される。

## WordPressなど既存プロジェクトへの影響

WordPress開発者向けメディアの記事によると、PHP 8.6のリリースはWordPress 7.2のRC1公開からわずか2日後というタイミングで行われた。WordPressは現在PHP 7.4を最低サポートバージョンとしており、2026年10月末時点でもPHP 7.4を使うサイトは約17%（2026年4月時点の20.5%から減少）に留まっている。WordPress側は既にPHP 8.6をPHPUnitのテストマトリクスに加えて移行作業を進めているが、記事は非推奨となった`spl_object_hash()`（2,359個のプラグインで8,772件使用）や`is_long()`（2,258個のプラグインで10,809件使用）など、既存プラグインへの影響が大きい非推奨APIを具体的に挙げ、開発者に対応を促している。また、ビルド・テストツールやPHPUnit、外部ライブラリ、URL・文字列処理、HTTP APIに関連する箇所も影響を受ける可能性があるとしている。

同時に記事は、PHP 8.6で追加された`Time\Duration`クラスや、PHP 8.5で導入されたURI拡張によるネイティブなURL処理など、WordPress本体の最低PHPバージョンが上がれば活用できる機能にも触れ、プレミアム機能を新しいPHPバージョンでのみ提供する「フィーチャーゲーティング」をアップグレードの動機づけとして提案している。PHP 8.6の正式リリースは、エコシステム全体にとって新機能の恩恵とレガシーコードの保守コストという両面の課題を同時に提示する節目になりそうだ。
