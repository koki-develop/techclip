# Microsoftの公式PyPIパッケージ「agent-framework」が改ざんされクレデンシャル窃取マルウェアが混入
Tags: Security, AI

- Microsoft's Agent Framework PyPI package compromised to steal credentials (2026-11-17)
  https://www.bleepingcomputer.com/news/security/microsofts-agent-framework-pypi-package-compromised-to-steal-credentials/
- Attackers Compromise Microsoft's Agent Framework PyPI Package to Steal Cloud Credentials (2026-11-18)
  https://thehackernews.com/2026/11/attackers-compromise-microsofts-agent.html
- Microsoft's official Python agent framework hijacked to distribute malware (2026-11-18)
  https://www.theregister.com/security/2026/11/18/microsofts-official-python-agent-framework-hijacked-to-distribute-malware/5310858

Microsoftの公式AIエージェントフレームワークのPyPIパッケージ「agent-framework」のバージョン1.26.1・1.26.2が改ざんされ、Python起動時に自動実行されるクレデンシャル窃取マルウェアが仕込まれていたことが判明した。AzureやGitHubなどの認証情報・トークン・環境変数が攻撃者のWebhookへ流出する仕組みが混入しており、サプライチェーン攻撃の新たな事例として注目されている。
