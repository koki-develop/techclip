# PyTorch LightningのPyPIパッケージにサプライチェーン攻撃、認証情報窃取バージョンが公開
Tags: Security

- PyTorch Lightning and Intercom-client Hit in Supply Chain Attacks to Steal Credentials (2026-04-30)
  https://thehackernews.com/2026/04/pytorch-lightning-compromised-in-pypi.html
- Malicious PyTorch Lightning Packages Found on PyPI (2026-04-30)
  https://www.sonatype.com/blog/malicious-pytorch-lightning-packages-found-on-pypi
- Shai-Hulud Themed Malware Found in the PyTorch Lightning AI Training Library (2026-04-30)
  https://semgrep.dev/blog/2026/malicious-dependency-in-pytorch-lightning-used-for-ai-training/

人気のPythonパッケージ「lightning」（PyTorch Lightning）に悪意のあるバージョン2.6.2と2.6.3が公開され、モジュールのインポート時に認証情報を自動窃取するサプライチェーン攻撃が確認された。PyPIによって当該バージョンは隔離されたが、AIモデル訓練環境を標的にした攻撃として注目されている。
