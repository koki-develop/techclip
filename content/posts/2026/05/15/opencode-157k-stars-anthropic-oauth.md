---
date: "2026-05-15T02:39:39+09:00"
title: "AnthropicのOAuth締め出しが招いた逆効果——OSSコーディングエージェント「OpenCode」が15万7000スターでClaude Codeを超える"
description: "AnthropicがClaude ProおよびMaxへのサードパーティOAuth認証をブロックし法的措置まで講じた結果、オープンソースのAIコーディングエージェント「OpenCode」の人気が爆発的に高まり、公式ツールClaude Codeを上回るGitHubスター数を獲得した。"
tags:
  - OSS
  - AI
references:
  - "https://thenewstack.io/anthropic-claudecode-opencode-split/"
  - "https://dev.to/pickuma/opencode-vs-claude-code-why-157k-developers-are-hedging-against-anthropic-2acb"
  - "https://byteiota.com/anthropic-blocks-claude-max-in-opencode-devs-cancel-200-month-plans/"
  - "https://github.com/anomalyco/opencode"
---

## 何が起きたのか

2026年1月9日、Anthropicはサーバー側のチェックを展開し、OpenCodeをはじめとするサードパーティツールがClaude ProおよびMaxのサブスクリプションをOAuth認証経由で利用することを突然ブロックした。警告や移行手順の案内は事前にほとんどなく、作業中だった開発者のワークフローが即座に寸断された。同年2月19日には利用規約の改定によってこの制限が正式化され、3月にはOpenCodeのリポジトリに対して法的要求が届いたことを示すコミット「anthropic legal requests」がマージされ、Claude Proへの認証コードがコードベースから完全に削除された。4月4日には、AnthropicのClaude Code責任者であるBoris Cherny氏がX上で「Claude ProおよびMaxのサブスクリプションはサードパーティツール経由での利用をカバーしない」と明言し、ポリシー変更が公式に確定した。

背景には技術的な問題があった。OpenCodeの初期バージョンは`claude-code-20250219`というベータHTTPヘッダーを偽装することで、Anthropicのサーバーに対してリクエストが公式CLI経由であるかのように見せかけていた。月額200ドルのMaxプランを含むサブスクリプション契約者が、実質的にOpenCode経由でClaudeを無制限に利用できていたわけだ。AnthropicはToS違反として「競合製品の構築」や「無断のサービス転売」を制限事項として挙げたが、自社の公式コーディングツールClaude Codeのリリース直後という時期もあり、競争上の動機が見え隠れする対応だったとして批判を浴びた。

## 開発者コミュニティの反応と皮肉な結果

ブロックによる開発者の反発は即座かつ激しかった。GitHubのイシューには147件以上のリアクションが集まり、Hacker Newsでは245ポイントを獲得した。「月額200ドルのMaxプランを解約した」「突然アクセスが切れて作業が止まった」といった声が相次ぎ、一部の開発者はCursorやGitHub Copilotなどのより安価な代替サービスへの移行を選んだ。

しかし最も注目すべき結果は、Anthropicの措置がOpenCode自体の人気をむしろ急騰させた点だ。2026年5月時点でOpenCodeのGitHubスター数は157,000を超え、Anthropicの公式`claude-code`リポジトリの約12万2,000スターを上回るまでになった。The New Stackが「157,000人の開発者がOpenCodeでAnthropicに対してヘッジしている」と表現したこの現象は、ベンダーロックインへの構造的な懸念が広く共有されていることを示している。開発者たちは「Anthropicが値上げした場合、規約を変更した場合、依存しているモデルが廃止された場合でも動き続けるツール」を求めているのだ。

## OpenCodeの技術的な特徴と競合優位性

OpenCodeは主にTypeScriptで書かれたオープンソースのターミナルベースAIコーディングエージェントで、SSTチームが開発・維持している。「100% open source」を掲げ、Claude・GPT-4・Gemini・ローカルモデルといった複数のLLMバックエンドに対応したモデル非依存アーキテクチャが最大の特徴だ。クライアント/サーバー構造のTUI（ターミナルユーザーインターフェース）を採用しており、コードがベンダーのサーバーを経由しないためプライバシー上の利点もある。

対するClaude Codeは、Anthropicモデルとの深い統合と低い初期設定コストが強みだが、利用できるモデルはAnthropicのものに限られる。The New Stack記事の著者はこの対立を「AIツール産業初の垂直統合対オープンアセンブリの分岐点」と位置づけ、単なるツール選択の問題ではなくベンダー依存のリスク管理という観点から開発者が判断を下していると分析した。

## 業界全体への波及とOpenAIの戦略的動き

Anthropicの規制直後、OpenAIは戦略的な動きに出た。OpenCodeをはじめOpenHands・RooCode・Clineなどのオープンソースツールに対してCodexサブスクリプションサポートを公式に拡張し、Anthropicが締め出した開発者コミュニティを積極的に取り込む姿勢を示した。これにより、AIコーディングツール市場における「オープンなエコシステムへの賭け」という文脈でOpenAIとAnthropicの対比が一層鮮明になった。

今回の一連の動きは、AI分野における「オープンAPI時代（2022〜2024年）」の終焉と、大手プロバイダーによるエコシステム囲い込みの本格化という大きなトレンドの一部でもある。OpenAI・Google・Microsoftも同様の傾向を示しており、開発者にとって「今後も使い続けられるツール」の選定が重要な意思決定となっている。157,000という数字は、一つの技術的成熟度を示す指標であると同時に、ベンダーリスクへの集合的な警戒心の表れでもある。
