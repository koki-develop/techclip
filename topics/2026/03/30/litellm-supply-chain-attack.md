# TeamPCPがLiteLLM PyPIパッケージを汚染、月間9500万DLのAIライブラリにマルウェア埋め込み
Tags: Security, AI

- TeamPCP Backdoors LiteLLM Versions 1.82.7–1.82.8 via Trivy CI/CD Compromise (2026-03-25)
  https://thehackernews.com/2026/03/teampcp-backdoors-litellm-versions.html
- LiteLLM Security Update March 2026 (2026-03-25)
  https://docs.litellm.ai/blog/security-update-march-2026
- Supply Chain Attack Hits LiteLLM: 95M Monthly Downloads at Risk (2026-03-25)
  https://www.helpnetsecurity.com/2026/03/25/teampcp-supply-chain-attacks/

TeamPCPと呼ばれる攻撃者グループが、Trivy CIパイプラインを悪用してAIエージェント向けLLMプロキシライブラリ「LiteLLM」のPyPIパッケージ（バージョン1.82.7・1.82.8）にバックドアを仕込んだ。SSHキーやクラウド認証情報を窃取するマルウェアが含まれており、月間約9,500万ダウンロードを誇る人気ライブラリだけに広範な影響が懸念される。悪意あるバージョンは公開から約3時間で隔離された。
