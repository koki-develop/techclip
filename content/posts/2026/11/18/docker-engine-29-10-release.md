---
date: "2026-11-18T18:09:22+09:00"
title: "Docker Engine 29.10.0リリース、Engine APIをOpenAPI 3.2へ移行し組み込みcontainerdのカスタマイズにも対応"
description: "Docker Engine 29.10.0が公開され、Engine APIのOpenAPI 3.2移行や組み込みcontainerdのカスタマイズ機能、実験的なジョブ管理機能などが追加された。"
tags:
  - OSS
references:
  - "https://docs.docker.com/engine/release-notes/29/"
---

## 概要

Dockerは11月16日、Docker Engine 29.10.0をリリースした。今回の目玉はEngine APIの仕様が長らく使われてきたSwagger 2.0からOpenAPI 3.2形式へ移行したことで、`api/openapi.yaml`として新たに提供される。互換性維持のため従来のSwagger 2.0仕様も引き続き生成されるが、今後のツール連携やドキュメント生成はOpenAPI 3.2が基準になっていく見込みだ。あわせてAPIバージョンはv1.57に更新された。

## 組み込みcontainerdのカスタマイズと実験的なジョブ機能

もう一つの大きな変更が、`/etc/docker/containerd.d/`配下にファイルを配置することで、Dockerに組み込まれたcontainerdの設定をカスタマイズできるようになった点だ。これまでDocker同梱のcontainerdは設定の調整余地が限られていたが、この仕組みにより運用環境に応じた細かなチューニングが可能になる。

さらに実験的な機能として、デーモンが直接管理するワンショットおよびcron的なスケジュールワークロードをサポートする「Jobs」機能が追加された。`--enable-extension org.mobyproject.jobs.v0`フラグで有効化する仕組みで、現時点では実験的な位置づけだが、Dockerデーモン単体で定期実行ジョブを扱える点は、外部のスケジューラやcronに依存していた既存の運用を簡素化する可能性がある。

## セキュリティ関連の破壊的変更とパッケージ対応拡大

今回のリリースでは、ローカルレジストリの扱いに関する破壊的変更も含まれる。従来はループバックアドレス(127.0.0.0/8および::1/128)上のレジストリは自動的に「insecure-registries」として扱われていたが、29.10.0以降はinsecure-registriesを明示的に設定している場合、この自動判定が適用されなくなった(設定を省略している場合は従来通り自動的にinsecureとして扱われる)。すでにinsecure-registriesを明示的に設定した上でHTTP通信や信頼されていないTLS証明書を使うループバックレジストリを利用している場合は、そのレジストリも明示的に`insecure-registries`へ追加する必要がある。セキュリティ強化の一方で、insecure-registriesを明示的に設定しているローカル開発環境では、設定の見直しが必要になる点に注意したい。

また、AlmaLinux・Oracle Linux・Rocky Linux向けの公式パッケージが新たに提供されるようになり、エンタープライズ向けLinuxディストリビューションでの導入がしやすくなった。このほかいくつかのバグ修正も行われている。

## 今後の展望

OpenAPI 3.2への移行は、APIクライアント生成やドキュメントツールとの連携を長期的に改善する基盤整備といえる。一方でローカルレジストリの扱いの変更は、CI環境やローカル開発でinsecure-registriesに依存している場合は移行時に設定の見直しが必要になるため、アップグレード前にリリースノートの確認が推奨される。
