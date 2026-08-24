---
date: "2026-08-24T20:06:58+09:00"
title: "WizのAIエージェント「Red Agent」がSnowflakeの脆弱性を発見、GitHub Copilot関与を巡り混乱も"
description: "セキュリティ企業WizのAIエージェント「Red Agent」がSnowflakeのGitHub Actionsワークフローに存在するスクリプトインジェクション脆弱性を発見し内部Jira環境への侵入を実証したが、脆弱性のコードがGitHub Copilotによって生成されたかどうかを巡り情報が錯綜した。"
tags:
  - Security
  - AI
references:
  - "https://www.wiz.io/blog/red-agent-snowflake-copilot-cicd-bug"
  - "https://www.forbes.com/sites/timkeary/2026/08/17/github-copilot-missed-a-vulnerability-that-wizs-ai-agent-found/"
  - "https://www.itpro.com/security/wiz-cto-speaks-out-amid-snowflake-github-flaw-confusion"
---

## 概要

セキュリティ企業Wizが開発した自律型AIセキュリティリサーチエージェント「Red Agent」が、Snowflakeの公開リポジトリ「snowflake-connector-net」のGitHub Actionsワークフローに存在するスクリプトインジェクション脆弱性を発見し、内部Jira環境の認証情報を窃取できることを実証した。Red Agentは2026年7月に一般提供が始まったばかりのツールで、人間の介入なしに脆弱性の発見から悪用までを自律的に実行できる。今回の発見では、GitHub Advanced Securityによるスキャンや、PRの共同作成者として関与していたGitHub Copilotのコードレビューでも見逃されていた脆弱性を突き止めた点が注目を集めた。Snowflakeは2026年6月23日にWizからの報告を受けて即座に脆弱性を修正し、翌6月24日には漏洩した可能性のある認証情報を無効化している。

## 技術的な詳細

問題の中心にあったのは`jira_issue.yml`というワークフローで、GitHub Issueのタイトルをエスケープ処理が不十分なままシェルスクリプトに直接埋め込んでいた。`TITLE=$(echo '${{ github.event.issue.title }}' | sed ...)`という記述はシングルクォートでタイトルを囲む設計だったが、攻撃者がタイトルにシングルクォートを含めることでこの保護を回避できた。さらに本来は`github.event.pull_request.user.login`を確認してホワイトリスト外のユーザーを弾くはずのセキュリティゲートも、Issueイベント発生時にはこの値が常に`null`となるため、実質的にすべてのユーザーが検査を素通りできる状態になっていた。Red AgentはこれらをGitHub Issueのタイトル経由で悪用し、`curl`コマンドでJira APIトークンをBase64エンコードして外部リスナーへ送信するペイロードを注入した。最初の試行は構文エラーで失敗したが、Red Agentは自律的にエラーを解析し、コマンドを修正して二度目で成功させている。窃取された認証情報は`qa@snowflake.net`アカウントに紐づき、エンジニアリングやセキュリティコンプライアンス、バグ報奨金追跡プロジェクトへの読み取りアクセス権限を持っていたが、監査ログによりアクセスしたのはWizのみであったことが確認されている。

## Copilot関与を巡る混乱

Wizは当初のブログ投稿で、この脆弱なコードがGitHub Copilotによって生成されたかのような表現を用いており、これが「AIが自ら脆弱性を作り出し、AIがそれを見逃した」という構図として大きく報じられた。しかしその後の詳細な調査で、実際に問題のコード行を書いたのはSnowflakeのエンジニアであり、Copilotは同じPR内の別の変更に共同作成者として関与していたに過ぎないことが判明した。Wizの共同創業者兼CTOであるAmi Luttwakはこの混乱について、Copilotを含む複数の貢献者が同じPRに関わっていたと説明した上で、「PRの共著者情報を見るだけでは、どの変更を人間が書き、どの変更をAIが書いたのかを正確に切り分けるのは難しい」と述べ、人間とAIの寄与を明確に区別することの困難さを認めている。一方でGitHub側は内部調査の結果として、脆弱性につながったコード変更は人間が作成したものでCopilotは関与していないと主張しており、両者の見解は完全には一致していない。

## 今後への影響

この一件は、AI支援開発の普及がソフトウェアの攻撃対象領域を急速に拡大させている実態を浮き彫りにした。セキュリティ専門家のErik Avakianは、従来型のセキュリティ運用がこうした変化に追いつけなくなりつつあると指摘し、攻撃側・防御側の双方がAIを駆使する「AI主導の戦場」が現実になりつつあると警鐘を鳴らしている。Wizの研究者Gal Nagliも、AI支援によるコード生成が攻撃面を広げる以上、防御側もAIによる自動脆弱性スキャンを先制的に活用すべきだと強調した。今回の事例はGitHub Advanced SecurityやCopilotのコードレビュー機能が、安全な`env:`変数と`jq`を用いたパターンから危険な直接文字列補間への変更を検知できなかったことも示しており、AIによる脆弱性発見・自動修正ツールの限界と、それを補う人間の監視体制の必要性を改めて浮き彫りにしている。
