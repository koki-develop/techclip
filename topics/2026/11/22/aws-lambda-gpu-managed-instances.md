# AWS Lambdaが、EC2 GシリーズによるGPUアクセラレーション対応のManaged Instancesをサポート開始
Tags: Cloud, AI

- AWS Lambda, GPU-accelerated Managed Instances (2026-11-18)
  https://aws.amazon.com/about-aws/whats-new/2026/11/aws-lambda-gpu-managed-instances/
- [Update] GPU Instances Can Now Be Used with Lambda Managed Instances (2026-11-18)
  https://dev.classmethod.jp/en/articles/lambda-managed-instances-gpu-acceleratorconfig/
- AWS Lambda Now Runs GPU Inference with 48 Concurrent Invocations Sharing One Model per GPU (2026-11-22)
  https://www.infoq.com/news/2026/11/aws-lambda-gpu-managed-instances/

AWS LambdaのManaged InstancesがEC2 Gシリーズを用いたGPUワークロードに対応し、vLLMやPyTorchなどのフレームワークをプリセットしたイメージを使ってAI推論やレンダリングをサーバーレスで実行できるようになった。1つのGPU上で最大48件の同時実行がモデルを共有できる構成となっており、サーバーレス環境でのAI推論コスト削減が期待される。
