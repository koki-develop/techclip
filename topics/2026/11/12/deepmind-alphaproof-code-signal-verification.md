# Google DeepMind、AI支援検証ツール「AlphaProof Code」でSignalプロトコルの安全性を形式的に証明
Tags: AI, Security

- Google DeepMind has successfully formally verified the security of the Signal protocol using 'AlphaProof Code' (2026-11-11)
  https://gigazine.net/gsc_news/en/20261111-google-deepmind-alphaproof-code-verification/
- Formal Verification of Signal's Protocol with Gemini (2026-11-10)
  https://deepmind.google/blog/introducing-alphaproof-code/
- Google DeepMind Uses AI Agents to Verify Signal's Core Machine Code (2026-11-10)
  https://www.unite.ai/google-deepmind-uses-ai-agents-to-verify-signals-core-machine-code/

Google DeepMindは、Geminiを活用したAIエージェント群「AlphaProof Code」を用いて、暗号化通信アプリSignalの実装(libsignal)を機械語レベルで形式検証したと発表した。転送秘匿性や認証といった安全性プロパティを600万行超のLean証明コードで証明し、わずか4週間、人間のレビューは1%程度という分業体制で達成したとしている。設計ではなく実際に稼働するコードレベルでの検証としては初の事例とされる。
