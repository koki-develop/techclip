---
date: "2026-09-21T08:10:25+09:00"
title: "セキュリティ研究者、Claude Opus 5でOpenAI従業員アカウントを72時間以内に侵害"
description: "Hacktron AIの研究者3人がAnthropicのClaude Opus 5を使い、libheifの脆弱性とSSOの欠陥を連鎖させてOpenAI従業員のChatGPTアカウントと内部GitHubへの侵入経路を確立した。"
tags:
  - AI
  - Security
references:
  - "https://techcrunch.com/2026/09/18/researchers-used-anthropics-claude-to-hack-into-openai/"
  - "https://venturebeat.com/security/openai-hacked-by-small-team-of-white-hat-security-researchers-using-anthropics-claude-opus-5"
  - "https://www.theregister.com/security/2026/09/18/researchers-used-claude-to-hack-openai-employees-chatgpt-accounts/5297517"
---

## 概要

セキュリティ企業Hacktron AIの研究者3人（Harsh Jaiswal氏、Mohan Pedhapati氏、Rahul Maini氏）が、AnthropicのClaude Opus 5を使ってOpenAIのバグバウンティプログラムに参加し、複数の脆弱性を連鎖させることでOpenAI従業員のChatGPT／Codexアカウントを乗っ取り、内部のGitHubリポジトリへのアクセス経路を72時間以内に確立し、実際に無害な変更を加えたプルリクエストを作成して実証した。ホワイトハットとしての正規の報告であり実害は生じていないが、最新の生成AIが脆弱性の発見からエクスプロイト開発までのハードルを劇的に下げつつある実例として、セキュリティ業界で大きな注目を集めている。

## 脆弱性チェーンの詳細

侵入の起点はOpenAIのコミュニティフォーラムで使われているDiscourse上のHEIC/HEIF画像アップロード機能だった。画像処理を担うImageMagickが内部で呼び出すlibheifライブラリにヒープバッファオーバーフロー（CVSS 8.8）が存在し、特別に細工した画像ファイルをアップロードするだけでリモートコード実行（RCE）が可能だった。これによりフォーラムサーバーを侵害した研究チームは、続いてOpenAIのシングルサインオン（SSO）実装の欠陥を突き、フォーラムの認証情報から従業員のChatGPT／Codexアカウントを乗っ取ることに成功。理論上はGitHub、Slack、メールなど、乗っ取ったアカウントに接続された社内サービス全般へアクセスできる状態だったという。

## AIモデルの進化がもたらした変化

このエクスプロイト開発における最大のポイントは、使用したAIモデルによって結果が大きく変わった点だ。研究チームは当初、旧モデルのClaude Opus 4.8でエクスプロイトの構築を試みたが失敗。ところが7月24日にリリースされたClaude Opus 5に切り替えたところ、わずか数時間で成功に至った。Hacktronの創業者Mohan Pedhapati氏は「AIはエクスプロイト開発に必要とされる希少な専門知識のハードルを下げており、かつて数ヶ月を要した作業が数日で完了するようになりつつある」と指摘する。Gray SwanのCEOも「月額200ドルのツールで誰もがOpenAI級の企業を攻撃できる時代になった」と警鐘を鳴らしている。

## 対応と今後の見通し

研究チームは7月25日にBugcrowd経由でOpenAIに脆弱性を報告し、OpenAIは報告から約14時間で対応、Discourse側も7月27〜28日にパッチを公開してサンドボックス対策を追加した。報奨金は6,500ドルだった。OpenAIは声明で、コミュニティ認証トークンの権限を制限し、影響を受けたトークンとセッションを失効させたと説明している。研究チームは「セキュリティ対策の前提を攻撃者の能力の進化に追いつかせる必要がある」と指摘する。一連の経緯は、企業に対して信頼できないファイル処理パイプラインの隔離、低レベル依存ライブラリへの迅速なパッチ適用、そしてAIエージェントの認証情報を特権アカウントと同等に厳格管理することの重要性を突きつけた。Claude Opus 5をめぐっては現時点で利用規制の議論が本格化しておらず、オープンウェイトモデルの能力向上とも相まって、国家規模の脅威アクターへの懸念も高まっている。
