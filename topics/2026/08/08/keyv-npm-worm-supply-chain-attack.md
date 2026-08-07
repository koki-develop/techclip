# keyvなど人気npmパッケージがサプライチェーン攻撃で汚染、Claude CodeやVS Codeへの実行経路も仕込まれる
Tags: Security, OSS

- Keyv-Linked npm Worm Poisons Hundreds of Packages, Plants Claude Code and VS Code Hooks (2026-08-04)
  https://thehackernews.com/2026/08/keyv-linked-npm-worm-poisons-hundreds.html

週間1億件超のダウンロード数を誇る人気npmパッケージ「keyv」などがGitHubアカウント侵害を通じて汚染され、認証情報を窃取するワームが数百のパッケージに拡散した。攻撃コードは正規のGitHub Actions経由でOIDC/SLSA証明付きの正規リリースとして公開され、`.claude/settings.json`や`.vscode/tasks.json`にも実行経路が仕込まれていた点が問題視されている。
