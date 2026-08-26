# 悪意あるWebページの閲覧だけでNVIDIA NemoClaw経由のローカルAIモデルが汚染される脆弱性
Tags: Security, AI

- A Malicious Webpage Could Poison Your Local AI Model Behind NVIDIA NemoClaw (2026-08-25)
  https://thehackernews.com/2026/08/a-malicious-webpage-could-poison-your.html
- Nvidia NemoClaw flaw let attackers poison the model behind a developer's AI agent (2026-08-25)
  https://siliconangle.com/2026/08/25/nvidia-nemoclaw-flaw-let-attackers-poison-the-model-behind-a-developers-ai-agent/

Oasis SecurityがNVIDIA NemoClawの脆弱性CVE-2026-65105を報告した。NemoClawはOllamaサーバーを認証なしで全ネットワークインターフェース(0.0.0.0:11434)上に起動するため、悪意あるWebサイトがDNSリバインディングを用いてブラウザのオリジンチェックを回避し、ローカルのAIモデルにアクセスできてしまう。この手法によりモデルのテンプレートに悪意ある指示を注入され、サーバーをリセットしても汚染が持続する恐れがある。NVIDIAは協調的な脆弱性開示を経てパッチを公開した。
