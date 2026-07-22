# GitHub Actions、「Pwn Request」対策の安全なデフォルト動作を全バージョンにバックポート
Tags: OSS, Security

- GitHub Actions gets secure-default CI/CD backport, shuts Pwn Request window (2026-07-20)
  https://www.techtimes.com/articles/321003/20260720/github-actions-gets-secure-default-ci-cd-backport-shuts-pwn-request-window.htm

GitHub Actionsのactions/checkoutにおいて、pull_request_targetやworkflow_runイベント内で未レビューのフォークPRコードをチェックアウトしようとするとワークフローを失敗させる新しいデフォルト動作が、7月16日付で全ての主要バージョンにバックポートされた。floatingタグ(例: @v4)を使うワークフローは自動的にこの変更を受け取り、「Pwn Request」型のサプライチェーン攻撃リスクを低減する。
