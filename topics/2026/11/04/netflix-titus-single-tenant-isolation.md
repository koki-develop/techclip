# Netflix、コンテナ基盤TitusにシングルテナントVM分離モードを追加し性能干渉を解消
Tags: Cloud

- Netflix Titus Adds Single-Tenant VM Isolation for Containers (2026-10-30)
  https://www.infoq.com/news/2026/10/netflix-titus-kubernetes-microvm/

Netflixが自社のコンテナ基盤「Titus」に、1つのタスクをEC2インスタンス単位で専有実行できるシングルテナントモードを追加した。従来の共有ホスト上でのマルチテナント実行では他タスクの負荷によって性能が不安定になる問題があり、専有実行によってノイジーネイバー問題を回避し、レイテンシに敏感なワークロードの安定性を高めることを狙っている。
