# GitHub Actions、サプライチェーン対策でpull_request_targetを12月2日からデフォルトブロック
Tags: OSS, Security

- pull_request_target blocked by default December 2 (2026-11-02)
  https://github.blog/changelog/2026-11-02-pull_request_target-blocked-by-default-december-2/

GitHubは2026年12月2日以降、パブリックリポジトリのGitHub Actionsにおいて`pull_request_target`イベントをデフォルトでブロックすると発表した。明示的に許可するActionsイベントポリシーを設定しない限り、フォークからのプルリクエストがシークレットや昇格した権限にアクセスできる同イベントは実行されなくなり、サプライチェーン攻撃のリスク低減を図る。
