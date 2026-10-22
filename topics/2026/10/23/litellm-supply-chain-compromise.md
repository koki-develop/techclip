# AIプロキシツールLiteLLMのPyPI・Dockerパッケージが乗っ取られ、認証情報窃取マルウェアとバックドアが配布
Tags: Security, OSS

- LiteLLM compromised in supply chain attack delivering credential stealer, backdoor (2026-10-22)
  https://www.helpnetsecurity.com/2026/10/22/litellm-compromised-supply-chain-attack-pypi-docker/
- LiteLLM Compromised in Supply Chain Attack Delivering Credential Stealer and Backdoor (2026-10-21)
  https://thehackernews.com/2026/10/litellm-compromised-in-supply-chain.html

AIプロキシツールLiteLLMのリリースパイプラインが侵害され、10月21日に悪意あるバージョン1.107.0がPyPIとDocker Hubに約2時間公開された。盗まれたGitHub CLIのOAuthトークンが原因とされ、AWSやAzure、AI関連の認証情報を狙う窃取型マルウェアとバックドアが仕込まれていた。LiteLLMが同種のサプライチェーン侵害に見舞われたのは今年2回目となる。
