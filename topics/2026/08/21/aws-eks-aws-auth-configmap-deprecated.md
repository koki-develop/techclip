# AWSが非推奨としたEKSの旧認証方式「aws-auth ConfigMap」、実に81%のクラスタが依然使用
Tags: Cloud

- AWS deprecated this EKS auth method. 81% of clusters still run it. (2026-08-19)
  https://thenewstack.io/kubernetes-fleet-security-management/

AWSはAmazon EKSの認証方式として旧来の「aws-auth ConfigMap」を非推奨とし、API駆動型の新方式（アクセスエントリー）への移行を推奨しているが、調査によれば実際にはEKSクラスタの81%が依然として旧方式を使用しており、大規模環境での移行の遅れとセキュリティ・運用上のリスクが浮き彫りになった。
