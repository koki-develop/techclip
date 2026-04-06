# Rustのドキュメントホスティング「docs.rs」がデフォルトビルドターゲットを5つから1つに削減
Tags: Programming Languages, OSS

- docs.rs: building fewer targets by default (2026-04-04)
  https://blog.rust-lang.org/2026/04/04/docsrs-only-default-targets/

Rustの公式ドキュメントホスティングサービス「docs.rs」が、2026年5月1日から既定でビルドするターゲットを5つから1つ（x86_64-unknown-linux-gnu）に削減すると発表した。ほとんどのクレートはターゲットごとに異なるコードをコンパイルしないため、ビルド時間とリソース消費を大幅に削減する変更となり、複数ターゲットが必要なクレートは設定ファイルで指定することで対応可能。
