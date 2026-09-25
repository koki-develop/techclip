# GKEがネイティブなスケールツーゼロ機能を追加
Tags: Cloud

- GKE adds native scale-to-zero capabilities (2026-09-23)
  https://cloud.google.com/blog/products/containers-kubernetes/gke-adds-native-scale-to-zero-capabilities

Google Kubernetes Engine(GKE)に、ワークロードのレプリカ数をゼロまでスケールダウンできるネイティブなスケールツーゼロ機能が追加された。HorizontalPodAutoscalerの`minReplicas: 0`設定とCloud Monitoringの外部メトリクスを組み合わせ、GKEが管理するキャパシティバッファを活用することで、コールドスタートなしで需要発生時に即座に再スケールできる点が特徴。これによりアイドル時のコスト削減とレスポンス性能の両立が期待される。
