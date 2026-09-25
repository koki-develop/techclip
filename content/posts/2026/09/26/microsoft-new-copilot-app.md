---
date: "2026-09-26T08:10:50+09:00"
title: "MicrosoftがCopilotを「Home・Code・Autopilot」の統合アプリに刷新、OpenAI・Anthropicへの対抗鮮明に"
description: "MicrosoftがChat・Cowork・Officeを束ねる新Copilotアプリを発表し、自然言語でアプリを作れるCodeと常駐型自律エージェントAutopilotを追加、OpenAIとAnthropicへの対抗を強めている。"
tags:
  - AI
references:
  - "https://www.geekwire.com/2026/microsoft-unveils-all-in-one-copilot-app-taking-on-anthropic-and-openai-in-new-push-to-boost-adoption/"
  - "https://blogs.microsoft.com/blog/2026/09/25/introducing-the-new-copilot-with-home-code-and-autopilot/"
  - "https://www.cnbc.com/2026/09/25/microsoft-copilot-ai-coding-anthropic.html"
---

## 概要

Microsoftは9月25日、Copilotを「Home」「Code」「Autopilot」の3本柱に再構成した新アプリを発表した。AI at Work担当CMOのJared Spataro氏がMicrosoft公式ブログで詳細を明らかにしたもので、従来別々だったChat、常駐エージェントのCowork、Word・Excel・PowerPointといったOfficeアプリの機能を単一の入り口に統合する。この刷新は、CEOのSatya Nadella氏が2026年6月に「夏までに」統合アプリを届けると公言し、7月の決算説明会でも「今四半期中」の投入を示唆していた約束を、会計年度第1四半期の締め切り(9月30日)まで1週間を切ったタイミングでギリギリ果たす形となった。

## Home・Code・Autopilotの機能

Homeは、会話形式で素早く回答や下書きを得られるChatモードと、複雑なタスクを一任できるCoworkモードを併せ持つ新しい起点で、Word・Excel・PowerPointの完全な機能をCopilot内に埋め込み、Office側との間でリアルタイムに同期する共同編集ドキュメントを生成できる。単純化されたビューアではなく、フル機能のOfficeアプリがCopilotの中で動く点が特徴だ。

Codeは、非開発者でも自然言語による指示だけでデスクトップウィジェット、対話型ダッシュボード、クラウドホスト型の社内アプリ、業務自動化ワークフローなどを構築できる機能で、GitHub Copilotと同じ基盤技術を採用し、テナント内のサンドボックス環境で動作する。新設の「Microsoft Copilot Managed Runtime」が安全なホスティングを担い、Power BIのセマンティックモデル2,000万件以上をCopilotに取り込む「Fabric IQ」や、Dynamics 365・Power Platformのデータ・ワークフローと連携することで、業務文脈を踏まえたアプリ生成を可能にする。

Autopilotは、ユーザーが作成・カスタマイズできる常駐型の自律エージェントで、Microsoft 365テナントのクラウド上で独立したID・メモリ・メールアドレスを持ち、TeamsやOutlookで同僚のように@メンションして仕事を依頼できる。サプライヤーレビュープロセス全体の管理のように、プロンプトなしで継続的にタスクをこなす運用を想定している。GeekWireによれば、これは2026年6月に「OpenClaw」を基盤として投入された常駐エージェント「Scout」の後継にあたり、Scoutというブランド名は廃止されてユーザーが独自に名付けるAutopilotに置き換わった。Copilot担当EVPのJacob Andreou氏は、長時間稼働する自律エージェント全般について「優れたエージェントの証である自律性と柔軟性こそが、IT管理者にとって恐ろしい存在にする要因でもある」と述べ、Autopilotがその懸念に応える設計だと説明した。Nadella氏は2026年3月、OpenClaw(2026年初めに話題になったオープンソースの個人向けエージェント)をセキュリティリスクとして「ウイルス」になぞらえており、ガバナンスを効かせた企業向け実装への転換が意識されている。

## モデル選択と料金体系、競合との位置づけ

新Copilotでは、OpenAIのGPT、AnthropicのOpus、システムが自動選択する「Auto」モードからモデルを選べるほか、MicrosoftのMAIモデルもスライドで言及されている。料金は、Chat・Word・Excel・PowerPoint・Outlook・Teamsでの利用をカバーする定額のユーザーサブスクリプションライセンス(USL)と、Cowork・Code・AutopilotによるエージェントワークやOpenAIの「Astra」・Anthropicの「Claude Fable」といったフロンティアモデル利用に課金する従量制(UBB)の二本立てで、管理者はAgent 365の管理ツールを通じて支出上限を設定でき、従量課金サービスはデフォルトで無効化されている。Nadella氏は「真の独立性とは、独自の評価基準を持ち、それをもとにモデルを乗り換えられることだ」と述べ、特定ベンダーへのロックインを避けたモデル横断の柔軟性を訴えた。GeekWireは、Microsoft幹部が機微なファイルをローカルマシンに送る運用(Anthropicの「Claude Cowork」の仮想マシン方式を念頭に置いたとみられる)を「完全に論外」と評したと報じており、セキュリティ面での差別化も強調されている。

Home・Codeはまず数週間以内にFrontierプログラムで先行展開され、Autopilotは月内に非公開プレビューへ拡大する。Microsoft 365 Premium/Proでのプレビューは2026年後半を予定する。背景には、2026年7月時点で有料のMicrosoft 365 Copilotシートが3,000万(4月時点の2,000万から増加)に達したものの、商用Microsoft 365の全シート数4億5,000万超に対する比率はなお約7%にとどまるという普及の遅れがある。Microsoft 365のクラウド収益は2026会計年度に約19%増の1,003億ドルに達した一方、Copilot単体の収益は開示されていない。Microsoftは財務報告体制も再編し、「Agents and Infra」セグメントを新設してGitHubのクラウド収益をMicrosoft 365事業に統合するなど、単一のアプリやサービス販売から「業務全体の連続性」を軸にした事業構造への転換を進めており、詳細は11月17〜20日にサンフランシスコで開催されるMicrosoft Igniteでさらに示される見通しだ。
