# pnpm 12.22.0がリリース、レジストリ変更時の検証スキップ脆弱性を修正
Tags: OSS

- Release pnpm 12.22.0 (2026-11-17)
  https://github.com/pnpm/pnpm/releases/tag/v12.22.0

パッケージマネージャーpnpmの新バージョン12.22.0がリリースされ、レジストリ変更時にminimumReleaseAgeやtrustPolicyの検証がスキップされてしまう脆弱性が修正された。合わせてグローバルパッケージ専用設定や`pnpm why --ranges`などの新機能も追加された。
