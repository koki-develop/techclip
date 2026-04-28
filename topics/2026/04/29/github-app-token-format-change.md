# GitHubがApp installationトークンのフォーマット変更を発表、4月27日より移行開始で既存の検証ロジック更新が必要
Tags: OSS

- Notice about upcoming new format for GitHub App installation tokens (2026-04-24)
  https://github.blog/changelog/2026-04-24-notice-about-upcoming-new-format-for-github-app-installation-tokens/

GitHubは2026年4月27日よりGitHub Appのインストールトークンのフォーマットを変更すると発表した。新フォーマットでは`ghs_APPID_JWT`形式に移行しトークン長が約520文字に拡張されるため、既存の検証ロジックや正規表現パターンを利用しているシステムは更新が必要となる。
