# GitHub Actions、サプライチェーン対策の「ワークフローロックファイル」機能が正式提供開始
Tags: OSS, Security

- GitHub Actions workflow lockfiles are generally available (2026-10-28)
  https://github.blog/changelog/2026-10-28-github-actions-workflow-lockfiles-are-generally-available/

GitHubは、Actionsワークフローの依存関係をコミットハッシュに固定する「ワークフローロックファイル」機能を、パブリックプレビューから約2週間で正式提供(GA)へ移行した。`gh actions-lock`CLI拡張を使い、タグやブランチ参照の見た目を保ちながら実体を固定コミットに紐づけることで、改ざんされたアクションを利用したサプライチェーン攻撃を防止できる。Dependabotと連携してロックファイルを自動更新する仕組みも備える。
